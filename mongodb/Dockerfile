# Base image
FROM 		clefos/clefos:clefos7

# The author
MAINTAINER 	The ClefOS Project <neale@sinenomine.net>
LABEL 		Vendor="ClefOS" License="GPLv2"

COPY		mongo.repo /etc/yum.repos.d/

RUN 		yum -y --setopt=tsflags=nodocs upgrade && \
		yum install -y --setopt=tsflags=nodocs -x "*v8*5.2.258-11*" mongodb-enterprise \
			mongodb-enterprise-server mongodb-enterprise-tools mongodb-enterprise-shell && \
		yum clean all && \ 
		rm -rf /var/cache/yum/* /tmp/* /var/log/yum.log

# Export MongoDB server port	
EXPOSE 		27017 28017

# Create volume for mongodb data folder
VOLUME 		/mongodb/data

# Command to start MongoDB daemon process
CMD 		mongod --dbpath /mongodb/data --verbose --ipv6 --bind_ip=0.0.0.0 --logappend --logpath /mongodb/data/mongodb.log
