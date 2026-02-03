---
layout: default
---

# Add a new user

Before proceeding, we need to check that we have sufficient privileges to be able to act on the required steps, and in this case, we need to check that we have the Global Administrator role.

Go to portal.azure.com > Entra ID (AAD) > under manage, select Roles and administrators.

![Admin Role Check](./admin_role_check.png)

Now that we have verified that we have sufficient privileges due to the assigned role, go to Entra ID (AAD) > under manage, select Users > select New user > Create new user. 

![Create New User 1](./create_new_user_1.png)

On the Create new user screen, enter the name of the user in both the UPN and Display name boxes > select Review + create (leave the remaining settings as they are, but you can make a note of the automatically generated password).

![Create New User 2](./create_new_user_2.png)

Select Create.

![Create New User 3](./create_new_user_3.png)

Repeat the above process for Dave and Jeff’s accounts, substituting the UPN and Display name values for their respective names.

# Create a group called DevSupport and add members

Next, we need to create a group for the new users we created in the above steps.

Go to portal.azure.com > Entra ID (AAD) > under manage, select Groups > select New group.

![Create New Group 1](./create_new_group_1.png)

Ensure that Security is selected under Group type, enter a name for the group under Group name, add a relevant description where needed into Group description, leave the Microsoft entra roles can be assigned to the group set to NO and the Membership type set to Assigned > select your own account as an Owner and the users that need to be assigned to the group as Members > select Create.

![Create New Group 2](./create_new_group_2.png)

![Create New Group 3](./create_new_group_3.png)

![Create New Group 4](./create_new_group_4.png)

Note: dynamic assignment wasn’t used in this instance but could be implemented by changing the Department attribute associated with each user entity, changing the Membership type of the group to Dynamic user, then adding a dynamic query.

![Create New Group 5](./create_new_group_5.png)

# Enable SSPR

Next, we need to enable the SSPR feature for the newly created security group.

Got to portal.azure.com > Entra ID (AAD) > under manage, select Password reset > select the Selected option under Self service password reset enable and select the previously created DevSupport group under the Select group heading > select Save.

[IMG]

[ADD SSPR CONFIG]

# Test SSPR

Next, we need to test that we’re able to utilize the SSPR functionality.

[IMG]

[IMG]

[IMG]

# Enable SSPR

Next, we need to enable and configure MFA for a user, then proceed to test that it’s working as expected.

Go to portal.azure.com > Entra ID (AAD) > under manage, select Security > under manage, select Multifactor authentication.

[IMG]

Select Additional cloud-based multifactor authentication settings.

[IMG]

Under the Users tab, select the user you need to enable MFA for, then select Enable MFA.

[IMG]

Select User MFA Settings, check the box next to Require selected users to provide contact methods again, then select Save.

[IMG]

Open a new incognito web browser window > go to https://aka.ms/mfasetup > attempt to sign in using the user’s username and password > click next through the Let’s keep your account secure, Install Microsoft Authenticator and Set up your account in app screens.

[IMG]

[IMG]

[IMG]

[IMG]

Open the Microsoft Authenticator app and scan the QR code > select Next, then enter the code presented > select Done.

[IMG]

[IMG]

[IMG]

To test that MFA is functioning as expected, close the incognito web browser window and open a new incognito web browser windows instance > go to myapps.microsoft.com > check to see if it prompts you for both your password and verification via the Microsoft Authenticator app.

[IMG]

Note: I haven’t included screenshots of this process for the users Jeff and John, but you’d just need to repeat steps 3 and beyond to do this. 

# Resources

* TBC

