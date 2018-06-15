# VoiceSleepLogger
Record Sleep-Log with Voice by Google Home &amp; IFTTT  
現在は日本語版で開発中ですが、原理上、言語を選ばずに可能です。  

# About (Demo)
[![VoiceSleepLogger](http://img.youtube.com/vi/zIuK77xYAjw/0.jpg)](http://www.youtube.com/watch?v=zIuK77xYAjw "VoiceSleepLogger")

# System Architecture
1. 「OK Google, おやすみ.」  
2. Awake Google Home and IFTTT
3. (IFTTT) Google Assistant, then, Google Spread Sheet
4. Write SpreadSheet
5. Trigger function in SpreadSheet by update event
6. ...zzz (sleep)
7. 「OK Google, おはよう！」  
8. Awake Google Home and IFTTT
9. (IFTTT) Google Assistant, then, Google Spread Sheet
10. Write SpreadSheet
11. Trigger function in SpreadSheet by update event
12. Trigger another webhook-function in SpreadSheet by update event
13. send request from SpreadSheet to IFTTT endpoint
14. webhooks, then write Google Calendar
15. Sleep-Log is recorded in Google Calendar!!

# Technique
## Default Google Home word
By default, 「おやすみ」 and 「おはよう」 are used by Google Assistant itself.  
But we can use it as our wake-word by ShortCut setting is Google Home app (in my case, iOS app).  
## SpreadSheet functions
Google App Scripts (GAS) can be used with SpreadSheet.  
And it contain trigger (event) system by default.  
So preprocessing, including formatting, is made by AGS and tiggered in response to update event.  
Update by function itself trigger udpate event, so I avoid the loop by flag as a cell.  
