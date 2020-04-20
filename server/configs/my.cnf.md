my.cnf
======

skip-external-locking                                                                                                                                 
skip-name-resolve                                                                                                                                     
                                                                                                                                                      
max_allowed_packet          = 16M                                                                                                                     
key_buffer_size             = 128M                                                                                                                    
innodb_buffer_pool_size     = 8G                                                                                                                      
innodb_log_file_size        = 1G                                                                                                                      
innodb_buffer_pool_instances = 8                                                                                                                      
innodb_buffer_pool_chunk_size = 134217728                                                                                                             
innodb_write_io_threads     = 2                                                                                                                       
innodb_read_io_threads      = 6                                                                                                                       
innodb_file_per_table       = 1                                                                                                                       
innodb_flush_method         = O_DIRECT                                                                                                                
innodb_log_file_size        = 1                                                                                                                       
innodb_flush_log_at_trx_commit  = 0                                                                                                                   
innodb_thread_concurrency   = 0                                                                                                                       
tmp_table_size              = 32M                                                                                                                     
max_heap_table_size         = 32M                                                                                                                     
table_open_cache            = 4000                                                                                                                    
                                                                                                                                                      
max_connections             = 160                                                                                                                     
query_cache_size            = 0                                                                                                                       
                                                                                                                                                      
performance_schema=ON                                                                                                                                 
                                      