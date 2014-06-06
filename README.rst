
startup gunicorn as service
====
Add python file as service in /etc/init.d/

example: /etc/init.d/myproj

    #!/usr/local/bin/python


    import sys, os
    
    from  gunicorn_service import ServiceSetting, gunicorn_service


    p = ServiceSetting(   work_dir="/home/WebServer/Server/Game/Game/",
                          bind_address="0.0.0.0:55555",
                          settings="Game.settings.local", 
                          name=os.path.basename(__file__), 
                          exe="/usr/local/bin/gunicorn" )


    gunicorn_service( p )

use service start| stop | stat, and try chkconfig myproj on 

