# timesheetSimon
<b>Description</b>:
A very simple Skype bot for timesheet reminder.

Below is the main function of the code. It may not be perfect but it does what I need and I thought it may be helpful. It is heavily based on the Azure example code.

On a Friday it prints "Reminder: Timesheets are due today" and on a Monday it prints "Reminder: Timesheets were due on Friday"- it prints these messages out 3 mins after it gets a message in that chat.

<b>Privacy</b>: It is your responsibility to get the code below reviewed for Privacy before you use this. As far as I am aware there is no data stored or shared that may be considered private. I am not liable for it's use or any impact coming from it's use.


<b>Terms of Use</b>: It is your responsibility to get the code below reviewed for Suitability before you use this. As far as I am aware there is no data stored or shared that may be considered private. I am not liable for it's use or any impact coming from it's use.


<b>Main function in the code.</b>
<pre>
var dateLastRun = new Date();
...
// Handle message from user
bot.dialog('/', function (session) {
    //session.send('dateLastRun at the start is : '+ dateLastRun);
    if (dateLastRun < new Date()) {
        var date = new Date();
        var day = date.getDay();
        if(day==1){//monday
            session.sendTyping();
            setTimeout(function(){ 
                session.send('Reminder: Timesheets were due on Friday');
            }, 180000);
            dateLastRun.setDate(dateLastRun.getDate() + 1);
        } else if(day==5){//friday
            session.sendTyping();
            setTimeout(function(){ 
                session.send('Reminder: Timesheets are due today');
            }, 180000);
            dateLastRun.setDate(dateLastRun.getDate() + 1);
        }
    }
    //session.send('dateLastRun at the end is : '+ dateLastRun);
             
});
</pre>
