headers
=======

    add_header Strict-Transport-Security "max-age=63072000; includeSubdomains; preload";
    add_header X-XSS-Protection "1; mode=block";
    add_header X-Frame-Options "SAMEORIGIN";
    add_header Referrer-Policy "no-referrer-when-downgrade";
    add_header X-Content-Type-Options nosniff;
    add_header Feature-Policy "midi none;microphone none;camera none;";
