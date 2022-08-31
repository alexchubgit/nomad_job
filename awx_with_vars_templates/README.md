## Resources
These files are required by awx. Download as artifact, or create in some other way

* '/etc/tower/conf.d/credentials.py.tpl'
* '/etc/tower/SECRET_KEY'
* '/etc/tower/conf.d/environment.sh'
* '/etc/nginx/nginx.conf'

## Using

`nomad job plan awx.job`
`nomad job run -check-index 0 awx.job`

***If nomad job already exits need to execute this command***
`nomad job stop -purge awx`

## Call AWX template with cURL 
`curl -f -k -H 'Content-Type: application/json' -XPOST --user admin:password http://192.168.56.62/api/v2/job_templates/ping/launch/`



***If low allocation memory for container <500Mb will be problems with processes inside container awx_task***



