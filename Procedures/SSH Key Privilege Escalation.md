
SSH Key PrivEsc

To perform this you need to have one condition, there being a .ssh folder in the user's home directory. Ideally the root user's home directory.

If there is one in place go ahead and change directories to it, give it a ls and look for a file titled "id_rsa".

Cat the file contents and copy them.

Now move over to your personal machine, you may want to create a new directory just to keep this new key away from all of your personal apps.

For an example procedure you'd do this

touch id_rsa
nano id_rsa
--paste contents into file including the header and footer of the key--
chmod 600 id_rsa

ssh <user>@10.10.10.10 -i id_rsa

don't forget to add the port flag if necessary. 

You should now be in as the corresponding user that you ripped the key from. Enjoy