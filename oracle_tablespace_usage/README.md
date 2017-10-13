Plugin for Oracle DB Monitoring
=====================================

For monitoring the performance metrics of your Oracle DB using Site24x7 Server Monitoring Plugins. Make sure you have the Site24x7 Linux server agent installed to add this plugin.
  

Prerequisites
=============

Ensure the following modules are installed to connect to the Oracle database:
    
    1. 	oracle-instantclient-basic-linux
	
	2.	oracle-instantclient-sdk-linux
	
    3.  cx_Oracle - python module
	
	In case you do not have the Oracle instant client installed already, you can install it by following the steps below:
	#Installing and configuring Oracle instant client
	================================================
	1. Dependencies
	Install the following packages
		apt-get install python-dev build-essential libaio1
	2. Download instant client for Linux x86-64 
		instantclient-basic-linux.x64-12.2.0.1.0.zip
		instantclient-sdk-linux.x64-12.2.0.1.0.zip  
	from Oracle Website (link : http://www.oracle.com/technetwork/topics/linuxx86-64soft-092277.html ). Please sign in to download
	3. Unzip and extract the downloaded zip files into a folder, and extract the zip files there.
	   for example, in a directory 
		mkdir -p /opt/oracle_client 
		
	4.Add environment variables:
   	   Create a file in /etc/profile.d/oracle.sh and add the following lines
		export ORACLE_HOME=/opt/oracle_client/instantclient_12_2
		export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$ORACLE_HOME
		
	   Create a file in /etc/ld.so.conf.d/oracle.conf  and add the following lines
		/opt/oracle_client/instantclient_12_2
	   	
	   Execute the command
		sudo ldconfig
		
		**Note: You need to Log out and log in,after this step for the changes to reflect**

	5. Create a symlink 
		cd $ORACLE_HOME
		ln -s libclntsh.so.12.1 libclntsh.so
		
	6. Install cx_oracle python using pip
		pip install cx_Oracle

Configure the agent plugin
==========================
 
1. Make the following changes in the oracle_tablespace_usage.py plugin file.
 
	    Change the values of ORACLE_HOST, ORACLE_PORT, ORACLE_USERNAME, ORACLE_PASSWORD and ORACLE_SID to match your configuration.
	    TABLESPACE_NAME - Enter the name of the TABLESPACEs you want to monitor. oracle_tablespace_usage plugin collects usage and status information of 
        all the Tablespaces mentioned in the "TABLESPACE_NAME" of the config section in the script.
 
2. To add the oracle_tablespace_usage.py plugin,
        
        1) Go to the agent installation directory
	        	cd /opt/site24x7/monagent/plugins/
	    2) Create a folder named oracle_tablespace_usage
		        mkdir oracle_tablespace_usage
	    3)Copy the plugin to this folder. (Note: The folder name and the plugin name should be the same)
	
The plugin will be added to the Site24x7 automatically. This might take about less than five minutes.


#Metrics Collected
===================
		*status - For all the Tablespace names configured in the "TABLESPACE_NAME" in the oracle_tablespace_usage.py script   
		*tablespace usage %  -  For all the Tablespace names configured in the "TABLESPACE_NAME" in the oracle_tablespace_usage.py script 
		
Using this you can monitor tablespace usage and configure alerts when a tablespace usage reaches the threshold.