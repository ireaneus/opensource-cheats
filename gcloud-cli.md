# Google Cloud SDK tools support two authorization methods:
User account authorization
  User account authorization is recommended if you are running a script or other automation on a single machine

Service account authorization
  Service account authorization is recommended if you are deploying a script or other automation across machines in a production environment. It is also the recommended authorization method if you are running gcloud commands on a Google Compute Engine virtual machine instance where all users have access to root.

  gcloud auth activate-service-account --key-file [KEY_FILE]

# GCLOUD CLI commands
gcloud
gsutil

# gcloud interactive - has auto prompting for flags, commands, and inline help
# to exit the shell type exit or Ctrl + q
gcloud components list
gcloud components install alpha
gcloud alpha interactive

# gcloud Compute commands
gcloud compute instances list --filter=name:instance1

# Core gcloud commands
gcloud init
gcloud auth list
gcloud config list
gcloud info
gcloud help compute instances create


gcl='gcloud '
gclal='gcloud auth login'
gclc='gcloud config '
gclcca='gcloud config configurations activate '
gclccc='gcloud config configurations create '
gclccl='gcloud config configurations list'
gclcl='gcloud config list'
gclcm='gcloud compute '
gclcms='gcloud compute ssh '
gclcs='gcloud config set '
jbnpr='gclcca mtl-nonprod-2b'
jbnpw='gclcca mtl-nonprod-2c'
jbpr='gclcca mtl-prod-1b'
