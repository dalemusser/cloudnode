# AWS Lightsail Unity WebGL Hosting

This document describes creating and using a Lightsail instance to host a Unity WebGL application.

## Create Instance

Platform: Linux/Unix

Select a blueprint: App + OS, Node.js (16.18.1-10) 
Note: this blueprint comes with Apache installed and operating.

Choose your instance plan: $10/month - Memory: 2 GB, Processing: 1 vCPU, Storage: 60 GB SSD, Transfer: 3 TB

Identify your instance: Unity-webGL-Hosting1

## Assigning Public Static IP Address

Go to the Lightsail dashboard and select *Networking*.

Create a static IP address and attach to the instance.

If a static IP address already exists, attach it to the instance.

## Assign Instance to Load Balancer

If there is a load balancer, set the target instance of the load balancer to the Unity-webGL-Hosting1 instance and attach.




