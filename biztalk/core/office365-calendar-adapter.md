---
title: 使用 Office 365 Outlook 行事曆配接器 |Microsoft Docs
description: 傳送和接收 BizTalk Server 中使用 Office 365 Outlook 行事曆配接器的訊息。 使用配接器使用接收埠的行事曆事件的接收和傳送埠，及建立和使用範例 XML 訊息建立行事曆事件。
ms.custom: ''
ms.date: 06/25/2018
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: MandiOhlinger
ms.author: ribarua
manager: dougeby
ms.openlocfilehash: ab724870e9c75a60119e86f7f62d6823f1db9873
ms.sourcegitcommit: e7609c319b64ec20bf215d17aa5ac4f9dcae52ec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36946169"
---
# <a name="create-calendar-events-with-the-office-365-outlook-calendar-adapter---biztalk-server"></a>使用 Office 365 Outlook 行事曆配接器-BizTalk Server 建立行事曆事件

使用 BizTalk Server 中的 Office 365 Outlook 行事曆配接器，建立並接收來自您 Office 365 Outlook 行事曆的行事曆事件。

## <a name="create-events-using-a-send-port"></a>建立使用傳送埠的事件

1. 在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，選取**新增**，然後選取**靜態單向傳送埠**。

    [建立傳送埠](../core/how-to-create-a-send-port2.md)提供一些指引。

2. 請輸入**名稱**。 在**傳輸**，將**型別**來**Office 365 Outlook 行事曆**，然後選取**設定**。

3. 選取 **[登入...**，並登入您的 Office 365 帳戶。 此帳戶是自動填入您的電子郵件地址。

4. 允許 BizTalk Server 的存取權限的核准：

    ![Office365 行事曆權限](../core/media/office365-calendar-permissions.png)

5. 設定您的 Office365 Outlook 行事曆預設屬性：

    |使用|以進行此動作|  
    |---|---|  
    | **行事曆** | 選取將在其中建立事件的行事曆。 |
    | **主旨** | 設定預設主體建立的事件。 （256 個字元的最大） |
    | **必要出席者** | 輸入以分隔您所需的預設出席者電子郵件地址 ';'。 （256 個字元的最大） |
    | **選擇性出席者** | 輸入的預設的選擇性出席者電子郵件以分隔的地址 ';'。 （256 個字元的最大） |

6. 選取行事曆： 

    ![Office365 行事曆](../core/media/office365-calendars.png)

    完成時，您的屬性看起來如下所示：

    ![端點屬性](../core/media/office365-calendar-send-properties.png)

7. 選取  **Ok**以儲存變更。

### <a name="test-your-send-port"></a>測試您的傳送埠

您可以使用簡單檔案接收埠和位置來建立 Office 365 Outlook 行事曆的事件。

1. 建立使用 File 配接器的接收埠。 內您接收位置，設定**接收資料夾**至 **C:\Temp\In\**，並將檔案遮罩設定為 **\*.xml**。
2. 在您的 Office 365 Outlook 行事曆配接器會將傳送埠屬性，設定**篩選條件**至`BTS.ReceivePortName == <Receive Port Name>`。
3. 將下列內容貼入文字編輯器，並將檔案儲存為**Office365Calendar.xml**。 這是您的範例訊息。

    ```xml
    <Event xmlns="http://schemas.microsoft.com/BizTalk/Office365OutlookCalendar/Send"> 
        <subject>Test event 1</subject> 
        <body> 
        <contentType>html</contentType> 
        <content>&lt;html&gt; 
        &lt;head&gt; 
        &lt;meta http-equiv="Content-Type" content="text/html; charset=utf-8"&gt; 
        &lt;meta content="text/html; charset=us-ascii"&gt; 
        &lt;/head&gt; 
        &lt;body&gt; 
        Test body for event Test event 1 
        &lt;/body&gt; 
        &lt;/html&gt; 
        </content> 
        </body> 
    </Event> 
    ```
    **在 < BizTalk 安裝 Folder\SDK\Schemas > SDK 的一部分提供的 XML 結構描述**

4. 啟動檔案接收位置和 Office 365 Outlook 行事曆配接器傳送埠。
5. 複製**Office365Calendar.xml**範例訊息至接收資料夾 (C:\Temp\In\)。 傳送埠會建立以 xml 為基礎的 Office 365 Outlook 行事曆中的事件。

## <a name="receive-events-using-a-receive-port"></a>使用 接收埠接收事件

1. 在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**接收連接埠**，選取**新增**，然後選取**單向接收埠**。

    [建立接收埠](../core/how-to-create-a-receive-port.md)提供一些指引。

2. 輸入名稱，然後選取**接收位置**。

3. 選取 **的新**，並**名稱**接收位置。 在 **傳輸**，選取**Office 365 Outlook 行事曆**從**型別**下拉式清單，然後選取**設定**。

4. 選取**登入...**，並登入您的 Office 365 帳戶。 此帳戶是自動填入您的電子郵件地址。

5. 允許 BizTalk Server 的存取權限的核准：

    ![Office 365 行事曆權限](../core/media/office365-calendar-permissions.png)

6. 設定**端點**屬性：

    |使用|以進行此動作|  
    |---|---|  
    | **行事曆** | 選取會從中提取事件的行事曆。  |
    | **正在啟動中** | 選取在其中行事曆事件必須以 （預設值為 15 分鐘） 的 biztalk 接收開始的時間間隔。  |

7. 選取行事曆：

    ![Office 365 行事曆](../core/media/office365-calendars.png)

    完成時，您的屬性看起來如下所示：

    ![端點屬性](../core/media/office365-calendar-receive-properties.png)

8. 選取  **Ok**以儲存變更。

### <a name="test-your-receive-settings"></a>測試您接收設定

您可以使用簡單的 File 傳送埠以接收來自您 Office 365 Outlook 行事曆的訊息。

1. 建立使用 File 配接器的傳送埠。 在您傳送連接埠的屬性，設定**目的地資料夾**至 **C:\Temp\Out\**，並設定和**檔案名稱**至 **%MessageID%.xml**.
2. 在您的檔案傳送埠屬性，設定**篩選條件**至`BTS.ReceivePortName == <Receive Port Name>`。
3. 開始 Office 365 Outlook 行事曆接收位置和 File 傳送埠。
4. 尋找目的地資料夾 (c:\temp\out) 中的訊息。 
**在 SDK 所包含的 XML 結構描述`\Program Files (x86)\Microsoft BizTalk Server <your version>\SDK\Schemas`。**

### <a name="example-of-a-received-calendar-event-xml"></a>已接收的行事曆事件 xml 的範例

```xml
<ns0:Event xmlns:ns0="http://schemas.microsoft.com/BizTalk/Office365OutlookCalendar/Receive"> 
<reminderMinutesBeforeStart>20160</reminderMinutesBeforeStart> 
<importance>normal</importance> 
<subject>Let's meet</subject> 
<id>AQMkADAwATNiZmYAZC0xMQBlOC0yODQ1LTA</id> 
<body> 
<contentType>html</contentType> 
<content>&lt;html&gt; 
&lt;head&gt; 
&lt;meta http-equiv="Content-Type" content="text/html; charset=utf-8"&gt; 
&lt;meta content="text/html; charset=us-ascii"&gt; 
&lt;meta name="ProgId" content="Word.Document"&gt; 
&lt;meta name="Generator" content="Microsoft Word 15"&gt; 
&lt;meta name="Originator" content="Microsoft Word 15"&gt; 
&lt;link rel="File-List" href="cid:filelist.xml@01D40724.27036CE0"&gt;&lt;style&gt; 
&lt;!-- 
@font-face 
  {font-family:"Cambria Math"} 
@font-face 
  {font-family:Calibri} 
p.MsoNormal, li.MsoNormal, div.MsoNormal 
  {margin:0in; 
  margin-bottom:.0001pt; 
  font-size:11.0pt; 
  font-family:"Calibri",sans-serif} 
a:link, span.MsoHyperlink 
  {color:#0563C1; 
  text-decoration:underline} 
a:visited, span.MsoHyperlinkFollowed 
  {color:#954F72; 
  text-decoration:underline} 
span.EmailStyle17 
  {font-family:"Calibri",sans-serif; 
  color:windowtext} 
.MsoChpDefault 
  {font-family:"Calibri",sans-serif} 
@page WordSection1 
  {margin:1.0in 1.0in 1.0in 1.0in} 
div.WordSection1 
  {} 
--&gt; 
&lt;/style&gt; 
&lt;/head&gt; 
&lt;body lang="EN-US" link="#0563C1" vlink="#954F72" style=""&gt; 
&lt;div class="WordSection1"&gt; 
&lt;p class="MsoNormal"&gt;Let’s sync up.&lt;/p&gt; 
&lt;/div&gt; 
&lt;/body&gt; 
&lt;/html&gt; 
</content> 
</body> 
<bodyPreview>Let’s sync up.</bodyPreview> 
<attendees> 
<type>required</type> 
<status> 
<response>none</response> 
<time>0001-01-01T00:00:00Z</time> 
</status> 
<emailAddress> 
<name>someone@contoso.com</name> 
<address>someone@contoso.com</address> 
</emailAddress> 
</attendees> 
<start> 
<dateTime>2018-06-25T17:00:00</dateTime> 
<timeZone>UTC</timeZone> 
</start> 
<end> 
<dateTime>2018-06-25T17:30:00</dateTime> 
<timeZone>UTC</timeZone> 
</end> 
<location> 
<displayName>Your office</displayName> 
<locationType>default</locationType> 
<uniqueId>Your office</uniqueId> 
<uniqueIdType>private</uniqueIdType> 
</location> 
<responseRequested>true</responseRequested> 
<seriesMasterId /> 
<isCancelled>false</isCancelled> 
<isOrganizer>true</isOrganizer> 
<createdDateTime>2018-06-18T23:48:35.0164728Z</createdDateTime> 
<lastModifiedDateTime>2018-06-18T23:48:22.178Z</lastModifiedDateTime> 
<hasAttachments>false</hasAttachments> 
<responseStatus> 
<response>none</response> 
<time>0001-01-01T00:00:00Z</time> 
</responseStatus> 
<changeKey>SFa3sLJfdiDEIpfwAAIAU=</changeKey> 
<originalStartTimeZone>Pacific Standard Time</originalStartTimeZone> 
<originalEndTimeZone>Pacific Standard Time</originalEndTimeZone> 
<isReminderOn>false</isReminderOn> 
<sensitivity>normal</sensitivity> 
<isAllDay>false</isAllDay> 
<showAs>busy</showAs> 
<type>singleInstance</type> 
<onlineMeetingUrl /> 
<recurrence /> 
<locations> 
<displayName>Your office</displayName> 
<locationType>default</locationType> 
<uniqueId>Your office</uniqueId> 
<uniqueIdType>private</uniqueIdType> 
</locations> 
<organizer> 
<emailAddress> 
<name>someone@contoso.com</name> 
<address>/O=FIRST ORGANIZATION/OU=EXCHANGE ADMINISTRATIVE GROUP(FYDIBOH3SPDLT)/CN=RECIPIENTS/CN=0003B11E8245</address> 
</emailAddress> 
</organizer> 
</ns0:Event> 
```

## <a name="next-steps"></a>後續的步驟
查看所有[Office 365 介面卡](office365-adapters.md)，或安裝[功能組件 3](https://aka.ms/bts2016fp3)。