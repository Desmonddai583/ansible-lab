Ansible Lab ENV setup steps

1. Once you install docker-toolbox, you'll need to use docker-machine to get a docker host vm up and running on virtualbox.
docker-machine create dev -d virtualbox

2. With docker-machine up, you can add the connection details to your shell:
eval "$(docker-machine env dev)"

3. Use an ssh keypair generator to create a keypair named ansible:
ssh-keygen -t rsa -f ansible

4. Copy the keypair you created in step 3 into the env/ subdirectory.

5. From the unpacked directory enter:
docker-compose build && docker-compose up

6. In another terminal session (or using an ssh client), connect to the hosts using the ansible key you created, and IP and Port mapping for the instance. Use docker-machine ip dev to print the IP for your docker host; the port mappings are found in the docker-compose.yml. You can also use the provided config file, by moving it to ~/.ssh/config on your local machine and updating the IP to match your docker host. Then you can simply ssh control to access the control host.