Practica 1
===========
Crear un aplicación y desplegarla en un PaaS. Usar cualquier lenguaje conocido. El objetivo de la aplicación puede estar relacionado con la asignatura y su material, por ejemplo, un interfaz REST al material de la misma o una mini-app para seleccionar PaaS basado en el lenguaje o los requisitos


Para la realización de esta practica me he basado en usar openshift ya que es una plataforma muy simple de usar y nos facilita el trabajo a la hora de crear la aplicación.
Lo primero que haremos sera entrar en la plataforma y crear una aplicación. En mi casa como lo que quiero montar es un blog basado en jommla, creare la aplicación con PHP y mysql.
Una vez realizado esto no disponemos a trabajar sobre openshift.

Primero deberemos instalar la herramienta de trabajo de openshift:
```
apt-get install ruby rubygems
gem install rhc

```
una vez instalado deberemos de configurar rhc

```
rhc setup 
OpenShift Client Tools (RHC) Setup Wizard

This wizard will help you upload your SSH keys, set your application namespace,
and check that other programs like Git are properly installed.

Using an existing token for xxxx@gmail.com to login to openshift.redhat.com

Saving configuration to /home/xxxx/.openshift/express.conf ... done

Checking for git ... found git version 1.8.1.2

Checking common problems .. done

Checking for applications ... found 2

Your client tools are now configured.

```
Una vez configurado deberemos crear un directorio local en nuestro ordenador sobre el cual trabajar.
```
mkdir joomla
cd joomla
git clone ssh://5261b1c54382ec217f00004a@joomla-josef267.rhcloud.com/~/git/joomla.git/
```

Una vez clonado el repositorio de openshift se nos crearan varias carpetas dentro de nuestra carpeta joomla
En mi caso la que me interesa es la carpeta php ya que es la que mostrara via web la instalacion de joomla.

```
cd php
wget http://joomlacode.org/gf/download/frsrelease/17715/77260/Joomla_2.5.8-Stable-Full_Package.tar.bz2
tar xvjf ../Joomla_2.5.8-Stable-Full_Package.tar.bz2
```
Despues de realizar esto nos disponemos a sincronizas nuestros ficheros con openshift
```
git add *
git commit -m "Primer commit"
git push
```

Una vez realizado esto nos disponemos a realizar la instalacion de Joomla en la direcion de openshift
```
http://joomla-josef267.rhcloud.com/
```
una vez configurado todo ya tendríamos joomla instalado y funcionando perfectamente para montar cualquier tipo de servicio web que necesitáramos.
En mi caso como ejemplo eh usado un plugin de joomla sobre github que podremos mostrar cualquier tipo de repositorio con sus documentos.
A parte podremos ver los documentos de los repositorios.

Tambien he creado un modulo propio para insertar cualquier tipo de texto o etiqueta rapida que necesitemos en ese momento en mi caso es un Hola mundo pero podria ser cualquier tipo de texto que necesitaramos introducir rapido.
Acontinuacion muestros los dos ficheros que se componen el modulo. Los ficheros osn un XML y un PHP
```
<?xml version="1.0" encoding="utf-8"?>  
<install type="module" version="1.5">  
  <name>Hola Mundo</name>  
  <author>josef267</author>  
  <creationDate>2013</creationDate>  
  <license>GPL</license>   
  <version>0.1</version>  
  <description>Modulo introduccion de texto</description>  
  <files>  
    <filename module="mod_holamundo">mod_holamundo.php</filename>  
  </files>  
</install>
```
Y este es el fichero php
```
<?php echo 'Hola mundo y hola clase de IV :)'; ?>

```
Despues de realizar estos dos ficheros los comprimimos en formato zip y lo instalamos como modulo y ya podremos usarlo tantas veces como nos haga falta de forma rapida

Bibliografia

https://albertomolina.wordpress.com/2012/12/26/instalacion-de-joomla-en-openshift/#more-931
http://extensions.joomla.org/extensions/social-web/social-display/documents-cloud-based/23764?qh=YToxOntpOjA7czo2OiJnaXRodWIiO30%3D
