   Prereq: gunicorn and github ssh and all that have been configed
   https://www.digitalocean.com/community/tutorials/how-to-serve-flask-applications-with-gunicorn-and-nginx-on-ubuntu-22-04#step-4-configuring-gunicorn
   1) git clone flask app
   2) make virtual env in flask app folder (python3 -m venv [ENVNAME]
   3) install flask by running pip install -r requirements.txt
   4) install gunicorn by running pip install gunicorn
   5) nano ~/[PROJECTNAME]/app/wsgi.py and paste the following:

from myproject import app

if __name__ == "__main__":
    app.run()

   6) edit your project's app.run() by replacing it with app.run(host='0.0.0.0')
   7) cry and sob because wtf is happening
