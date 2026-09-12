# Operation Dead Deploy: Conducting an investigation into an Interns mistakes

## Scenario
An intern with temporary contributor access deployed a “Test Environment” over the weekend. Didn’t follow policy setting up the environment and left once complete. Conducting the investigation the intern created a governance failure with naming policy not followed with an audit effect rather than a deny effect. This in turn allowed the environment to be created without being blocked.

## Environment
 Multi-User Azure training tenant, read only access.

## Investigation
With this first action we are investigating the resource groups to see if anything is new. We see off the rip that one resource group does not follow the naming convention of rg-workload_id-env_indicator-region-instance_number.<img width="521" height="32" alt="Screenshot 2026-09-12 115610" src="https://github.com/user-attachments/assets/04c455d0-cc7a-4330-9949-22ddcb5f6926" />


With the next step we are seeing what is inside the group, the intern only deployed one item. On the left hit the tags menu and you’ll see there are tags available for the resource. This tag is what is used for the intern to document stuff internally.<img width="582" height="345" alt="Step 2 redacted" src="https://github.com/user-attachments/assets/1831389a-78f1-4475-9847-7daa90f666d1" />


Now we will see where the resource came from. Checking the deployment tab on the left under “Settings” drop down you’ll see where it has the deployment name. As we see here it also does not follow naming convention.<img width="950" height="662" alt="Screenshot 2026-09-12 094524" src="https://github.com/user-attachments/assets/74105ad6-27dd-435e-bb2c-fec37c33da70" />

According to MadHat Labs, there should be a policy following naming convention. We can inspect if this is active for this interns resource group they created. Under the “Settings” drop down you’ll see “Policy” Clicking that you’ll see it says “Non-Compliant”. Going to the “Assignments” drop down under “Authoring” you’ll see where under Assignments Name it says naming convention.<img width="933" height="663" alt="Screenshot 2026-09-12 095138" src="https://github.com/user-attachments/assets/5b3e2feb-681d-49c3-a647-4f887b786653" />

Under scope it says Policy. Click the Naming Convention. Under Parameters in the bottom you’ll see the Value is “Audit” Audit allows a resource to be created without following policy and it’s just flagged. This is suppose to be “Deny” which never would’ve allowed the RG to be created not following the governance.<img width="583" height="596" alt="Step  6 redacted" src="https://github.com/user-attachments/assets/4dcd6b6a-059b-4470-99db-8542beda1bdc" />




## What broke / what surprised me
The most credible section in the document. Dead ends, wrong guesses, the thing that took an hour. Employers know real work is messy. This section separates you from certificate collectors.When I did this twice, I forgot to document the first go around and had to go back through. The second time around the intern tag wasnt there but it let me populate the info into the field for the screenshot. I have pretty good knowledge on Azure and navigating it. The thing that was new for me was the policies and how they work. Knowing the differences between them and following compliance and governance made me feel like I was actively learning something then using it versus learn and move on. Audit allowing things to be created but flagged and Deny not allowing it at all makes complete sense and will be retained due to this lab. My employer doesn’t follow the naming convention like the Azure environment here. But it is still easy to navigate and find the ones I have access to.





## Findings and recommendations
Update needed for naming convention policy effect type from “audit” to “deny”

• This would be a learning experience for the intern who created the resource group. Educate the intern on what he/she did wrong.


• Speak to the person who is in charge of the intern and checking what the intern has done in the environment before they leave for the weekend to prevent issues such as this.


•Review who holds the contributor access and for how long


•If deployment is in audit document why it's intentional versus the normal policy




## What I learned
In this investigation I learn about resource hierarchy and naming convention.



• I learned about the use and reasoning for tags. Tags can provide valuable information on the item in question.


• I learned about the use and reasoning behind deployment records. The deployment record can provide valuable information like who created the resource. You can then match to see what they did and makes the investigation easier.
 
 
 • I learn about Azure Policy, audit and deny. These two rules’ effects used to control how Azure responds when a resource doesn’t follow policies set. Audits allow the resource to be created or changed, but Azure flags it so it can be reviewed. Deny works by preventing the resource from being created or changed if it violates the policy. 
