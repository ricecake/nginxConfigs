server {
	listen [::]:80;
	listen [::]:443 ssl;
	server_name maestro.tfm.nu;

	location /ws/ {
		send_timeout 48h;
		proxy_read_timeout 48h;
		proxy_pass http://127.0.0.1:8001;
		proxy_http_version 1.1;
		proxy_set_header Upgrade $http_upgrade;
		proxy_set_header Connection "upgrade";
	}
	location / {
		proxy_pass http://127.0.0.1:8001;
		proxy_set_header X-Real-IP $remote_addr;
		proxy_set_header Host $host;
		proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
	}
}
