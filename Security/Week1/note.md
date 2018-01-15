#user authentication notes


## create a user with all privilege

``mongo admin -u alice -p secret 
``


## create a user with all privilege

``db.createUser({user:'alice',pwd:'secret',roles:['root']})``

