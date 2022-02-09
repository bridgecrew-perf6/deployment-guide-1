# deployment-guide
This is my take on a guide to explain how to deploy the jobs and contracts to get a plugin node ready
Node Oracle Deployment Guide

First of all we need to install the Browser Plugin „XDCpay“. Create a Wallet and send some XDC and PLI there. 5 of each will be completly fine for you to get the idea.

After setting up the wallet,  we need to add an adress to it for the deployment to work.
 

**Step 1:**

Press on the Menu (1) to open the „Wallet Options“. Then press on „Settings“ (2) to see the following:
 
<img width="296" alt="Step1" src="https://user-images.githubusercontent.com/95173225/153218302-c320fb35-bf71-40aa-b86d-d1fa0f87936c.png">
 
Enter the „New RPC URL“ ( https://erpc.xinfin.network/ ) and press „save“

<img width="276" alt="Step2" src="https://user-images.githubusercontent.com/95173225/153218356-49e719a9-d0cf-4602-b2bf-fb44301afa23.png">

You should now see the following:
 
<img width="247" alt="Step3" src="https://user-images.githubusercontent.com/95173225/153218401-e77e6518-984d-461f-b13e-f14211782d78.png">

**Step 2:**

Open https://remix.xinfin.network/ in the same browser in which you have set up your XDCpay Wallet.

Open the „Oracle.sol“ as shown below. If it´s not there for you, just create a new file with this name. Thats just as fine.

<img width="989" alt="Step4" src="https://user-images.githubusercontent.com/95173225/153218478-27c54fec-93a3-42e4-a13a-1b83e10922cd.png">

Paste the following code snippet into the fresh file or check the content to appear as shown below:
Code:

    pragma solidity 0.4.24;
    import "@goplugin/contracts/src/v0.4/Oracle.sol";

**Step 3:**

First get into the „Solidity Compiler“ (1)
Check if the compiler (2) has the same version as shown in the code (3).
 
<img width="629" alt="Step5" src="https://user-images.githubusercontent.com/95173225/153218761-ad229167-275a-438f-8780-244aa34274da.png">

Click „Compile Oracle.sol“ (1) and see that the logo shows a green checkmark (2)
  
<img width="525" alt="Step6" src="https://user-images.githubusercontent.com/95173225/153218790-edc6046b-002d-432c-a8ee-3a74e4d7888d.png">

**Step 4:**

Click onto the „Deploy & run transactions“ (1) button.
Check that enviroment is „Injected Web3“ (2)
Check that your wallet adress is shown (3)
Paste the PLI Smart Contract ( 0xff7412ea7c8445c46a8254dfb557ac1e48094391 ) adress into the „Deploy“ form (4)
Press „Deploy“ (5)
 
<img width="613" alt="Step7" src="https://user-images.githubusercontent.com/95173225/153218812-abfc453a-7d5e-43c2-9bd8-8b0703cd20c1.png">

You are asked to confirm a transaction. Feel free to press „Submit“
 
<img width="262" alt="Step8" src="https://user-images.githubusercontent.com/95173225/153219021-46094e13-ab28-44fd-ab23-1ae06a56a50c.png">

After submitting the transaction you should see this:

<img width="762" alt="Step9" src="https://user-images.githubusercontent.com/95173225/153219044-ed3e7333-d764-4094-aca2-e76dac0595b3.png">

In the output part the bottom of your webbrowser.
(If not, make sure you have selected the https://erpc.xinfin.network/ node in you wallet)

Now click on the output (1) and copy your transaction hash (2)
 
<img width="745" alt="Step10" src="https://user-images.githubusercontent.com/95173225/153219075-6679aef5-a78a-4208-8eea-ac1f6fea67ca.png">


Go to https://explorer.xinfin.network/ (1)

 
And paste the tx-hash into the searchbox (2). Then click on the „search“ button (3).

<img width="691" alt="Step11" src="https://user-images.githubusercontent.com/95173225/153219127-4f81c6d9-bf96-4a56-8eda-b0d0595e6ff7.png">

You`re now directed to a detailed overview regarding the transaction. Here you can see the Contract that has been created. Copy and store it somewhere because you need it later and for submitting the node when you´re finished.

<img width="713" alt="Step12" src="https://user-images.githubusercontent.com/95173225/153219199-88e4857b-67de-4e5a-977c-78f18edbcc11.png">


**Step 5:**


Log into your nodes dashboard. You´ll get there by typing http://your-ip:6688/ into your browser. If you have any problems getting there, make sure youre firewall on the servers allows the port 6688 ingoing. If it is not enabled, check log files and status of your node.
You can do that by using the following commands on the vps shell:
! „plinode“ is the name of my docker container. It may varies to yours. Maybe you even have no name for your container. You can check the name or ID of your container with the following command: 
docker ps -a
sudo docker exec -it plinode /bin/bash -c ". ~/.profile && pm2 status"
sudo docker exec -it plinode /bin/bash -c ". ~/.profile && pm2 log 0" or 1 depending on which logs you want to access.
If you installed the node via script, you just need to use the following command:
pm2 status
pm2 logs 0/1

If you made it to the dashboard of your node, you`re looking at this:
Click on „Keys“
 
<img width="1201" alt="Step13" src="https://user-images.githubusercontent.com/95173225/153219248-9b788f85-4a64-43b7-9807-39e6e8d3015b.png">

The top adress is the „Node Wallet Adress“ (1) you´ll also need later when submitting the node. Store it somewhere to get back to fast.
Click on the button to copy the adress (2) because you need to fund the node now with 1 xdc and 1 pli in order to allow the node to send transactions and pay the fee for it. Right now the Balance is 0 (3).
 
<img width="1241" alt="Step14" src="https://user-images.githubusercontent.com/95173225/153219265-41db4452-40c9-4efd-8c07-4e7cae2f5a8d.png">

Open the XDCpay Wallet and press on „send“. Just send 1 xdc for now. 
 
Next chose „Tokens“ (1) from the bottom list and then press on the Menu (2) 
 
<img width="248" alt="Step17" src="https://user-images.githubusercontent.com/95173225/153219398-d847e765-0f82-4e57-94ab-65224561342f.png">
 
And „send“ on the next window.
 
<img width="262" alt="Step16" src="https://user-images.githubusercontent.com/95173225/153219437-f429b72a-88ed-4ad4-aa96-fd1aa1e7e0a4.png">

After you successfully sent 1 xdc and 1 pli you should now see the balance on your node:
<img width="1227" alt="Step18" src="https://user-images.githubusercontent.com/95173225/153219472-50adc299-5c8b-4dc9-9337-5abcc9217266.png">

**Step 6:**

Get back to your browser and click on the dropdown button to validate your node on the blockchain.
 
<img width="220" alt="Step19" src="https://user-images.githubusercontent.com/95173225/153219648-e2dcb99e-d626-48c1-833b-1c8fe9059b33.png">

In the „setFulfillment…“ Form you paste your nodes wallet adress in the following form: „adress“,true (1). Then Press the button (2)
 
<img width="207" alt="Step20" src="https://user-images.githubusercontent.com/95173225/153219674-5c7a0573-b5a5-4f3c-ae3c-7322224d94c4.png">

Once again you´re asked to confirm a transaction which you should do in order to proceed.
 
<img width="233" alt="Step21" src="https://user-images.githubusercontent.com/95173225/153219740-a416e7b7-8816-4e2b-8445-c7c993da0ecc.png">

Confirmation of a successfull transaction is shown on the bottom again.
 
<img width="817" alt="Step22" src="https://user-images.githubusercontent.com/95173225/153219775-3d88461f-2057-4084-afb8-233506e6642c.png">

**Step 7:**

Next thing we need to do is to deploy a test job. In this case a simply Alarm Clock job.

First we alter this code:

    {
        "initiators":[
            {
               "type":"external",
               "params":{
         "name": "xdc",
                  "body": {
         "endpoint": "xdc",
         "addresses": ["0xf180e56bb575806aefaf2a7616622a9fc180b51c"]
        }
               }
           }
       ],
       "tasks":[
           {
               "type":"sleep",
               "confirmations":null,
               "params":{
                }
            },
            {
                "type":"ethbool",
                "confirmations":null,
                "params":{
                }
            },
            {
                "type":"ethtx",
                "confirmations":null,
                "params":{
                }
            }
        ],
        "startAt":null,
        "endAt":null
    }

 
Like this:
Name (1) and endpoint (2) need to be the same (for docker installations, and how you named it. In my example it is „pluginei“)
„Adresses“: (3) needs to be the oracle adress you received in Step 4. 
 


Go to your nodes dashboard and click on „Jobs“ (1) and then on „New Job“ (2) 

Paste your edited code:
 

Hit „Create Job“ when youre ready.
 
 
If everything is fine, you should see this:

 

Next click on „Definition“ (1) and copy the Job ID like shown below (2).
 

 
Step 8:
Go back to your browser (remix.xinfin.network)
Click on the „RequestContract.sol“ file. If there is none. Just create it yourself.
 

 
Here we need to paste the following code:


 
Edit it, so that it looks like this:
In oracle=YOURCONTRACTADRESS, paste yours (1)
Same goes for jobId=YOURJOBID. Its the ID we just got from creating the AlarmClock Job.
 

This will create the AlarmClock Contract. So that the job can get triggered.

After checking and editing the code you can hit the „Compile RequestContract.sol“ button. Please check the Compiler Version the same way you did for the „Oracle.sol“

 
 
On the „Deploy & Run Transactions“ Tab you check for „Enviroment“ to be „Injected Web3“ (1), Account to be your Wallet adress (2), that your AlarmClockSample is selected as „Contract“ (3) and that you put the PLI Smart Contract Adress ( 0xff7412ea7c8445c46a8254dfb557ac1e48094391 ) into the „Deploy“button Form (4).
 
Hit „Deploy“ and confirm the transaction with „submit“.
 
The output should show as the following:
 

 
Now you need to copy the transaction hash again like before:
 

Go to https://explorer.xinfin.network , paste the hash and hit „search“.

 
 
Copy the adress that got created:
 
And fund it with 1 pli. We do that because now, the transaction gets triggered by the contract we just created. And to be able to make a transaction on the blockchain it needs to pay its fee.
Go to your wallet, select your pli token and send the token to the adress we just created.
 




Make sure the right wallet is selected (1), the receipient ist he contract we just got from the xinfin explorer and you dont send more than 1 pli. Less would also be ok, but we want to be on the safe side for now (and with the current prices of 1 token)
 
After the transaction is confirmed and submitted, click on the dropdown arrow fort he AlarmClockSample.
 

In the form for „requestAlarm“ put a „2“ (1) and hit the „requestAlarm…“ button (2).

First of all the successfull transaction should be shown as output in your browser.
 

 
And you should be able to see the triggered job at your nodes dashboard under „Jobs“ and „Runs“.
 
If you did everything accordingly, the result will be this:
 


Thats it. You finished setting up the node. Its now ready to be submitted on your plugin dashboard which you can access via https://oracles.goplugin.co/

Congratulations!
