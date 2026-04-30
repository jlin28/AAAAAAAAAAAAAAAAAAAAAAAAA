This guide assumes you've already done the steps in https://www.digitalocean.com/community/tutorials/how-to-serve-flask-applications-with-gunicorn-and-nginx-on-ubuntu-22-04#step-4-configuring-gunicorn and got it working

1) Run ```git clone <FLASK_APP>``` on ur home page (or whatever page but do home page cause that's how I did it)
2) Go into Flask app: ```cd <FLASK_APP>```
3) Make virtual env in Flask app folder: ```python3 -m venv <ENV>``` and run it with ```source <ENV>/bin/activate```
4) Install Flask by running ```pip install -r requirements.txt```
5) Install gunicorn by running ```pip install gunicorn```
6) Run ```nano wsgi.py``` and paste the following: (NOTE: `<SUBDIRECTORY>` refers to if your `__init__.py` is somewhere like `~/<FLASK_APP>/app/__init__.py` and can be disregarded if its not)

```
from <SUBDIRECTORY>.__init__ import app

if __name__ == "__main__":
    app.debug = False
    app.run(host='0.0.0.0')
```
6) (OPTIONAl MAYBE) Edit your `__init__.py`'s `app.run()` by replacing it with `app.run(host='0.0.0.0')`
7) Allow access to port 5000 with ```sudo ufw allow 5000```
8) Configure Gunicorn by running ```gunicorn --bind 0.0.0.0:5000 wsgi:app```. If this step doesn't work, try seeing if your python file runs normally with ```python app/__init__.py```.
9) Run ```sudo nano /etc/systemd/system/<FLASK_APP>.service``` and paste the following: (You need to `CTRL + \` (replace) `<USER>, <FLASK_APP>, and <ENV>` with the right names)

```
[Unit]
Description=Gunicorn instance to serve <FLASK_APP>
After=network.target

[Service]
User=<USER>
Group=www-data
WorkingDirectory=/home/<USER>/<FLASK_APP>
Environment="PATH=/home/<USER>/<FLASK_APP>/<ENV>/bin"
ExecStart=/home/<USER>/<FLASK_APP>/<ENV>/bin/gunicorn --workers 3 --bind unix:<FLASK_APP>.sock -m 007 wsgi:app

[Install]
WantedBy=multi-user.target
```
9) Configure Nginx with ```sudo nano /etc/nginx/sites-available/<FLASK_APP>``` and paste the following:

```
server {
    listen 80;
    server_name _ _;

    location / {
        include proxy_params;
        proxy_pass http://unix:/home/<USER>/<FLASK_APP>/<FLASK_APP>.sock;
    }
}
```
10) Delete other files in /etc/nginx/sites-available (for some reason I didn't need to do this??!?!)
11) Run ```sudo ln -s /etc/nginx/sites-available/<FLASK_APP> /etc/nginx/sites-enabled```
12) Run ```sudo systemctl restart nginx```
13) Run ```sudo ufw delete allow 5000```
14) Edit the ```app.secret_key``` var in `__init__.py` to a static var instead of `os.random()`.
15) Get the newest version running with ```sudo systemctl restart <FLASK_APP>```
