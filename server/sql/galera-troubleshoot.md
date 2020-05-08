galera-troubleshoot
===================


После аварийного выключения всех нод, восстановление нужно начинать с той что выключилась последней

It may not be safe to bootstrap the cluster from this node. It was not the last one to leave the cluster and may not contain all the updates. To force cluster bootstrap with this node, edit the grastate.dat file manually and set safe_to_bootstrap to 1

<https://www.symmcom.com/docs/how-tos/databases/how-to-recover-mariadb-galera-cluster-after-partial-or-full-crash>

Если осталась одна нода, в автоматическом режиме:

    MariaDB [(none)]> set global wsrep_provider_options='pc.bootstrap=YES';
    
    
The cluster address shouldn't be empty like gcomm://. This should never be hardcoded into any configuration files. 

wsrep_provider_options
A useful option to set is pc.wait_prim=no to ensure the server will start running even if it can't determine a primary node. This is useful if all members go down at the same time.