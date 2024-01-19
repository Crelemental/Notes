
![[Pasted image 20231008132526.png]]
**Buffer Overflows** occur when you don't properly account for the size of the data input into your applications. If an application accepts data, most programming languages will require you to specify the amount of data you take in (*bounds checking*), you might receive 1000 character when you only had storage for 50. The extra data may overwrite other areas in memory that are used by other applications or the OS. Some languages like Java and C# implement bounds checking.

**Race Conditions** occur when multiple processes control or share access to a resource and the correct handling of that resource depends on the proper ordering or timing of transactions. 

**Input Validation Attacks**
	If you're not careful to validate the input to your applications, ie its in a acceptable format, you might fall victim to problems like a format string attack.
	*format string attacks,* attackers use certain print functions within a programming language that are meant to format the output but instead allow the attacker to manipulate or view and application's internal memory. Attackers could use %n or special parameters to access parts of memory that they normally cant access, just through the input. 

**Authentication Attacks**
	Those that attempt to gain access to resources without the proper credentials to do so. 

**Authorization Attacks**
	Attacks that attempt to gain access to resources without the appropriate authorization to do so. You should authenticate against a remote server or on the hardware of the device if its portable so that you get more control. 

**Cryptographic Attacks** 
	Easy to implement badly, and gives a false sense of security. You shouldn't try implementing your homegrown cryptographic algorithm even if it may have some security benefit. You should also make it easy to change to different algorithms easily and possible to change encryption keys if they get exposed or change.

**Client Side Attacks (WEB)**
	Takes advantage of weaknesses in the software loaded on the user's clients or rely on social engineering to fool the user.
	**Cross-site scripting XSS** is an attack carried out by placing code written in a scripting language into a web page, or other media such like Adobe Flash animation, that's displayed by a client browser. When others view the webpage/media, the code executes automatically and the attack is carried out.
	IE: The attacker may leave a comment containing the attack script in the comments section causing people that visit the page to execute the attack.
	**Cross-site request forgery and clickjacking** are also client side attacks. 

**Server Side Attacks (WEB)**
	*Directory Traversal Attacks* is a example of what happens if you dont validate input into your web apps. Attackers can use these attacks to gain access to the file system outside of the web server's structure where content is stored. "../" character allows to move up a level of directory allowing to view outside content. ![[Pasted image 20231008134810.png]]
	You just need to filter out special characters to fight off this type of attack

**Improper or Inadequate Permissions**
	There can be configuration files that hold the credentials and app uses to access a database. If these files and the dir that hold them arent properly secured, attacker may simply read your credentials from the file and access the database as they please.

**Database Security**
	![[Pasted image 20231008150313.png]]![[Pasted image 20231008150321.png]]

![[Pasted image 20231008150922.png]]
![[Pasted image 20231008151019.png]]
#ITSec

