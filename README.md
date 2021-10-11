# Task-given-by-Mahesh
Metadata is "data that provides information about other data",[1] but not the content of the data, such as the text of a message or the image itself. There are many distinct types of metadata, including


What is matadata in GCE? 
Google Cloud Platform provides a metadata server that knows details about your App Engine instance, such as its containing project ID, service accounts, and tokens used by the service accounts. You can access this data using simple HTTP requests: no client libraries are required.

Why it's is used in GCE? 
The metadata server provides information about a VMs scheduling option through the scheduling/ metadata directory entry and the maintenance-event attribute. You can use these metadata values to notify you when a maintenance event is about to happen so that you can prepare your environment for the event.

What is a startup script?? 
A startup script is a file that performs tasks during the startup process of a virtual machine (VM) instance. Startup scripts can apply to all VMs in a project or to a single VM. Startup scripts specified by VM-level metadata override startup scripts specified by project-level metadata, and startup scripts only run when a network is available. This document describes how to use startup scripts on Linux VM instances. For information about how to add a project-level startup script, see gcloud compute project-info add-metadata.


While creating an instances through the command line we can develope the equivalent command line from the GCP console. While developing we have to enter the start up script to udate the system. 
The script is as follows in the bin bash :
![IMG-20211010-WA0002](https://user-images.githubusercontent.com/92073323/136691284-0712bc6d-4769-4c6b-8150-fb021331017a.jpg)



#! /bin/bash
 apt update
 apt -y install apache2
 cat <<EOF > /var/www/html/index.html
 <html><body><p>Linux startup script added directly.</p></body></html>

  ![IMG-20211010-WA0003](https://user-images.githubusercontent.com/92073323/136691439-b8c9eef1-d732-4b74-b723-b3b6d8f6bf5b.jpg)


  

This will update the system instance while creating the instance through command line. 
Then while creating the instance we can add on  more scripts to make them vm more flexible. 
Like for example we can delete, stop, create, start the instance from there itself. For that a startup script is needed. The script is as follows :

#!/bin/bash
var='please enter your choice'
options= ("opt1-Delete" "opt2-Stop" "opt3-start" "quit")
select opt in "${options[@]}"
do
case $opt in
"opt1-Delete")
echo "choose 1"
gcloud compute instances delete fizan
echo "your instance is deleted"

"opt2-Stop")
echo "choose 2"
gcloud compute instances stop fizan
echo "instance stopped"
;;
"opt3-start")
echo "choose 3"
gcloud compute instances start fizan
echo "instance started"
;;
"quit")
break
;;
*)echo "invaild option";;
esac
done
  ![IMG-20211010-WA0005](https://user-images.githubusercontent.com/92073323/136691468-a7a0dd27-26b8-40f5-ab39-30ba0dd7fa7d.jpg)
  ![IMG-20211010-WA0004](https://user-images.githubusercontent.com/92073323/136691478-68ea9e84-a585-4b00-ae79-bd55edcfc9bf.jpg)




This script will create the following options in the instance like to delete, stop, start, create a particular instance.
