Encryption based security and hardware isolation based security are both needed because they both ofer different commercial, space and time based advantages/disadvantages

Using Apple iPhones as an example,
- Hardware isolation based security 
	- Offers good security but has more overhead
	- e.g. secure enclave
		- Main job of the secure enclave is to...?
		- isolated hardware can still communicate with each other?
	- Separation of responsibility, one to take care of encryption/decryption of instructions (AES engine), needs it to be fast 

Replay attack -> use session key/nonce, a time based method to add to the required request, which is unique and known only to the user at the time

## Data protection
- CPU has a privilege level of -1, and we cannot be sure that the os is not malicious. Therefore, when OS need the encrypted data to be decrypted, as requested by the user, we  have to ask the cpu to decrypt on the behalf of the OS.
- Chain of encrypted keys:
	- Ka (where a is a random file)> Kdpk + size, name > Kfs (file system)> EK
	- Got difference between Kdpk and Kfs because we want to have a difference in level of privileges -- dont need to know the Ka but want to know about the size, name
- To read K_{fs}, which is encrypted by K_{aes}, which is a unique value to each boot time
	- When we need K_{fs}, the cpu will get the encrypted version of K_fs and get the AES Engine to decrypt it
		- Therefore, OS can only see encrypted K_fs
		- Whenever OS need to see something that is encrypted by K_fs, it will do a syscall to the CPU, CPU talk to AES engine to get the decrypted content, then return the decrypted content to OS
	- This channel between Main CPU and AES engine is in plaintext, so it should be secured by hardware isolation.
		- Means that there is a way for the hardware to know if it is being tampered with
- To read Ka, the encrypted Ka is given to the enclave, which has the K_dpk key.  
	- Then Enclave encrypt the Ka to the OS with (Kaes)
	- The OS will recover the Ka by doing a system call to main CPU to talk to the AES Engine to decrypt the Ka

## Comparison
Mobile phones only have one user, while computer OS can have multiple users accessing the same file. Now, it is the mobile phone that defines which app can accept which apps. Developers need to think his/her app, what permissions from other apps are needed

## App Security
- Manifest file to store permissions?
- When app requests access to another app2, it sends a intent message to the reference monitor
	- Components
	- Action
	- Data
- Component Label pairs
- Reference Monitor to keep track of the permissions granted for all apps
- difference between activity and permissions? 

## Access Control
- Mandatory vs Discretionary Access Control
- For example -- Mobile app is mandatory
	- Set of permissions for the files are set in the manifest -- user can only choose a subset of permissions that were written in the manifest. Manifest file cannot be changed
	- You cannot add or delete permissions, just choose a subset of permissions defined in the Manifest

## Android related
- If user permissions are not specified in the manifest, then the app will fail at install time
- There are two different ways of getting another component to run from my application
	- Direct access -- kinda like syscall
	- Indirect access -- also known as the Intent
		- If the intent is explicit, we name the target component
		- If the intent is implicit, we will broadcast to ask anyone who has the component that we want
			- Note that if app 1 calls app 2 to run a component (e.g camera), then app 2 will run the camera, even if app 1 does not have the permissions for it in its manifest document
- There are different types of protection, such as signature level protection?
- 
#ss