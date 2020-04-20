nginx-snippets
==============
**static**

        location ~* \.png$  { access_log off; log_not_found off; expires max; gzip off; }
        location ~* \.jpg$  { access_log off; log_not_found off; expires max; gzip off; }
        location ~* \.jpeg$ { access_log off; log_not_found off; expires max; gzip off; }
        location ~* \.gif$  { access_log off; log_not_found off; expires max; gzip off; }
        location ~* \.ico$  { access_log off; log_not_found off; expires max; gzip off; }
        location ~* \.woff$  { access_log off; log_not_found off; expires max; gzip off; }
        location ~* \.woff2$  { access_log off; log_not_found off; expires max; gzip off; }
        location ~* \.ttf$  { access_log off; log_not_found off; expires max; gzip off; }
        location ~* \.svg$  { access_log off; log_not_found off; expires max; gzip off; }
        location ~* \.xml$  { access_log off; log_not_found off; expires max; gzip off; }
        location ~* \.mp4$  { access_log off; log_not_found off; expires max; gzip off; }

        location ~* \.css$ { access_log off; expires 7d; log_not_found off; add_header Vary Accept-Encoding; }
        location ~* \.js$  { access_log off; expires 7d; log_not_found off; add_header Vary Accept-Encoding; }