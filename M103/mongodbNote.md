# mongod initiation code

  * configure mongod in command shell

  ``mongod --port 30000 --dbpath first_mongod --logpath first_mongod/mongod.log --fork``

  * configure mongod via config file  

  ``  mongod -f mongod.conf``

  * sample config file

  ``
  storage:
    dbPath: "/var/mongodb/db"
  systemLog:
    path: "/var/mongodb/db/mongod.log"
    destination: "file"
    logAppend: true
  net:
    bindIp : "192.168.103.100,127.0.0.1"
    port: 27000
  security:
    authorization: enabled
  processManagement:
    fork: true
  operationProfiling:
    mode: "slowOp"
    slowOpThresholdMs: 50
  ``
