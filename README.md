# G1ANT-facebook
Facebook Addon for G1ANT Studio

# How to use:

## `getfriends` and `getposts` Commands:

1.  First, you need a [Facebook Developer Account](https://developers.facebook.com). 
2. Next, create a Facebook App from the "My Apps" dropdown at the https://developers.facebook.com/ site.
3. After you have created your app, Go to the [Graph API Explorer](https://developers.facebook.com/tools/explorer/) page.
4. Click the "Get Token Button" and then Click "Get User User Access Token".
5. Click the "user_friends" checkbox in the "Select Permissions" menu and click "Get Access Token".
6. Click the "Continue As" button to allow access.
7. Copy the string in "Access Token" text box. 
8. In G1ANT Studio, use the command `facebook.getfriends` to get the names of the friends for the specified user.
9. Use the command `facebook.getposts` to get the last 10 posts by the user. 
10.  Give the Access Token that you previously copied as the parameter "accesstoken" to both the commands. The command should return a JSON response which can be displayed using the dialog command. 
## `makepagepost` Command

1. To use the `makepagepost` command, you need the page access token to a page you admin. In the Graph API Explorer, similar to getting the user access token, Click the same dropdown and get the "page access token" option.

2. This command requires both the `manage_pages` permission and `publish_pages`. `publish_pages` can be obtained by clicking on the dropdown and selecting "Request publish_pages".

3. `makepagepost` requires an additional parameter "ID", this is the ID to your page. You can get your ID from the Graph API inspector by typing "/me/" in the textbox next to the Submit button after you have generated a page access token.

4. `makepagepost` requires another parameter "message", this specifies the message you want your post to contain. 

5. Finally, the `result` variable contains the ID of the post that was made if the posting was successful. 

6. Note that a single page access token gives access only to a specific page, you would need to generate a new  token to gain access to a different page.

## `makegrouppost` Command
1. `makegrouppost`can use the same access token as `getfriends` and `getposts` but it requires the "publish_to_groups" permission.
2. It takes three parameters: "accesstoken", "message", "id"; "accesstoken" contains the accesstoken, "message" is the message the post should contain. "id" is the ID of the group. The ID can be obtained from the Graph API inspector by typing in "me/?fields=groups" and clicking submit. It should return the IDs of all the groups  you are in.
3. `result` returns the ID of the post made to the group if it was successful.

## `getgroupposts` and `getpageposts` Commands
1. `getgrouposts` command takes three parameters: "accesstoken", "id", "numberofposts"; "accesstoken" is the User access token that can be used with `getfriends`, `getposts` commands etc., "id" specifies the ID of the group to retrieve posts from, "numberofposts" specifies the number of posts to retrive. 

2. `getpageposts` takes the same parameters but uses a different "accesstoken" i.e., the page access token used for `makepagepost` command.

3. Both commands return JSON response in the `result` variable. 

## `groupinvite` Command
1. `groupinvite` command takes six parameters: "groupid", "friendname", "email", "password", "type", "search".
2. "groupid" is used to identify the group, the group ID used for `getgroupposts` and `makegroupost` can be used here. 
3. "friendname" contains the name of the friend to be invited to the group. 
4. "email" contains the login e-mail ID to be used to log in to Facebook.
5. "password" contains the password to use to log in to Facebook.
6. "type" is used to specify the type of browser to open up Facebook in.
7. "search" is a parameter required by selenium, this can be set to any text, this will get replaced internally. 
8. This command opens up a new browser with the URL to the group.


**Note:** Access Tokens do not provide permanent access to the data, you would need to generate a new token or extend the existing token for the commands to remain functional. 


# Acknowledgements

Uses code from the [G1ANT repository](https://github.com/g1ant-robot). 