# novel_plus has a stored XSS vulnerability

## desc

There is a stored XSS vulnerability in novel_front. When modifying the user name, although verification is done to limit the content of the user name, there is no verification or insufficient verification in the background, allowing attackers to modify the uploaded content through packet capture. This results in a stored XSS vulnerability,

At the same time, because the administrator did not perform verification when viewing the user list in the background, the malicious JS submitted by the attacker will be executed in the background.

## Verify

Just register an account, we can see that the user nickname here is our mobile phone number

![image-20231228145013250](./assets/image-20231228145013250.png)

Then click Modify, we can see that there are some prompts telling us that we can only include content such as Chinese characters.

![image-20231228145120331](./assets/image-20231228145120331.png)

You can see that I modified it above to get the value of my own cookie, and then submitted it and you can see that the pop-up window started in front.

![image-20231228180734371](./assets/image-20231228180734371.png)

![image-20231228180829770](./assets/image-20231228180829770.png)

After that, we logged in to the administrator backend and accessed the member management interface, and found that the JS code we submitted had also been executed.

![image-20231228180948831](./assets/image-20231228180948831.png)

An attacker can use this to try to obtain the administrator's cookie and log in to the backend.

## Repair suggestions

- Try to verify the front and back ends together
- Use HTTPOnly testing or SameSite policy
- HTML encoding of display content