# replica set initiation code



  1.  Creating the keyfile and
``sudo mkdir -p /var/mongodb/pki``

  2.  check and setting permissions on it
  ``ls -l -p /var/mongodb/pki
    sudo chown vagrant:vagrant -R /var/mongodb
    openssl rand -base64 741 > /var/mongodb/pki/m103-keyfile
    chmod 600 /var/mongodb/pki/m103-keyfile
  ``

  3.  create mongodb directory
  ``sudo mkdir -p /var/mongodb/db/node1
    sudo mkdir -p /var/mongodb/db/node2
    sudo mkdir -p /var/mongodb/db/node3``

  4.  setting permissions
  ``sudo chown vagrant:vagrant -R /var/mongodb/db/node1
    sudo chown vagrant:vagrant -R /var/mongodb/db/node2
    sudo chown vagrant:vagrant -R /var/mongodb/db/node3``

  5. prepare config file and revise content(dbpath,port,logpath)
  [sample replica set config file](./node1.conf)
  ``cp node1.conf node2.conf
    cp node2.conf node3.conf
  ``

  6.  initiation replica set nodes
  ``mongod -f node1.conf
    mongod -f node2.conf
    mongod -f node3.conf
  ``

  7.  Connecting to node1:
  ``mongo --port 27011``

  8.  Initiating the replica set:
  ``rs.initiate()``

  9.  Creating a user:
  ``db.createUser({
  user: "m103-admin",
  pwd: "m103-pass",
  roles: [
    {role: "root", db: "admin"}
  ]
})``

  10. Exiting out of the Mongo shell and connecting to the entire replica set:
  ``mongo --host "m103-example/192.168.103.100:27011" -u "m103-admin"
-p "m103-pass" --authenticationDatabase "admin"``

  11. add other nodes
  ``rs.add("m103.mongodb.university:27012")
rs.add("m103.mongodb.university:27013")``
