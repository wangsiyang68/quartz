# Selenium
---
Things you could do: Check if the links are working
- Automate the clicking of link, and checks whether link return a HTTPS(200) response
	- The selenium code when run will open a browser and perform the tasks. Good to use thread.sleep(N) so that you can watch the stuff being clicked?
- Repeat the first task for every link found on every page
	- by specifying `By.tagName("a")` in `driver.findElements`
	- Need to reload all the links after pressing back button
	- Need to check for stale Elements
- Can minimize and maximize the browser window
- Can use it to brute force find the password? xD
- Help to login w user name and password
	- need to check for the case when user enter wrong username/pw combi
		- As a result, use `WebDriverWait(driver, time (in secs))` to wait for the event of page loading successfully
- Monkey Testing links
	- Good idea to check if links are broken #todo what is the difference between broken link and stale link
	- Can close the page and do the link pressing in command line check if response is 200
#webp 