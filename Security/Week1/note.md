#user authentication notes


## successfully auth in mongo shell

* ``mongo admin --eval "db.auth('alice','secret');db.runCommand({getParameter: 1, authenticationMechanisms: 1})" ``
* ``mongo admin -u alice -p secret --eval "db.runCommand({getParameter: 1, authenticationMechanisms: 1})"``
* ``mongo -u alice -p secret  --eval "db=db.getSisterDB('admin');db.runCommand({getParameter: 1, authenticationMechanisms: 1})" --authenticationDatabase admin``






## create a user with all privilege

``db.createUser({user:'alice',pwd:'secret',roles:['root']})``

