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
# <a name="create-calendar-events-with-the-office-365-outlook-calendar-adapter---biztalk-server"></a><span data-ttu-id="0e10e-104">使用 Office 365 Outlook 行事曆配接器-BizTalk Server 建立行事曆事件</span><span class="sxs-lookup"><span data-stu-id="0e10e-104">Create calendar events with the Office 365 Outlook Calendar adapter - BizTalk Server</span></span>

<span data-ttu-id="0e10e-105">使用 BizTalk Server 中的 Office 365 Outlook 行事曆配接器，建立並接收來自您 Office 365 Outlook 行事曆的行事曆事件。</span><span class="sxs-lookup"><span data-stu-id="0e10e-105">Use the Office 365 Outlook Calendar adapter in BizTalk Server to create and receive calendar events from your Office 365 Outlook Calendar.</span></span>

## <a name="create-events-using-a-send-port"></a><span data-ttu-id="0e10e-106">建立使用傳送埠的事件</span><span class="sxs-lookup"><span data-stu-id="0e10e-106">Create events using a send port</span></span>

1. <span data-ttu-id="0e10e-107">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，選取**新增**，然後選取**靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="0e10e-107">In the BizTalk Server Administration console, right-click **Send Ports**, select **New**, and select **Static One-way send port**.</span></span>

    <span data-ttu-id="0e10e-108">[建立傳送埠](../core/how-to-create-a-send-port2.md)提供一些指引。</span><span class="sxs-lookup"><span data-stu-id="0e10e-108">[Create a Send Port](../core/how-to-create-a-send-port2.md) provides some guidance.</span></span>

2. <span data-ttu-id="0e10e-109">請輸入**名稱**。</span><span class="sxs-lookup"><span data-stu-id="0e10e-109">Enter a **Name**.</span></span> <span data-ttu-id="0e10e-110">在**傳輸**，將**型別**來**Office 365 Outlook 行事曆**，然後選取**設定**。</span><span class="sxs-lookup"><span data-stu-id="0e10e-110">In **Transport**, set the **Type** to **Office 365 Outlook Calendar**, and select **Configure**.</span></span>

3. <span data-ttu-id="0e10e-111">選取 **[登入...**，並登入您的 Office 365 帳戶。</span><span class="sxs-lookup"><span data-stu-id="0e10e-111">Select **[Sign in …**, and sign in to your Office 365 Account.</span></span> <span data-ttu-id="0e10e-112">此帳戶是自動填入您的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="0e10e-112">The account is auto-populated with your email address.</span></span>

4. <span data-ttu-id="0e10e-113">允許 BizTalk Server 的存取權限的核准：</span><span class="sxs-lookup"><span data-stu-id="0e10e-113">Allow BizTalk Server approval for permission to access:</span></span>

    ![Office365 行事曆權限](../core/media/office365-calendar-permissions.png)

5. <span data-ttu-id="0e10e-115">設定您的 Office365 Outlook 行事曆預設屬性：</span><span class="sxs-lookup"><span data-stu-id="0e10e-115">Configure your Office365 Outlook Calendar default properties:</span></span>

    |<span data-ttu-id="0e10e-116">使用</span><span class="sxs-lookup"><span data-stu-id="0e10e-116">Use this</span></span>|<span data-ttu-id="0e10e-117">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="0e10e-117">To do this</span></span>|  
    |---|---|  
    | <span data-ttu-id="0e10e-118">**行事曆**</span><span class="sxs-lookup"><span data-stu-id="0e10e-118">**Calendar**</span></span> | <span data-ttu-id="0e10e-119">選取將在其中建立事件的行事曆。</span><span class="sxs-lookup"><span data-stu-id="0e10e-119">Select the calendar in which events will be created.</span></span> |
    | <span data-ttu-id="0e10e-120">**主旨**</span><span class="sxs-lookup"><span data-stu-id="0e10e-120">**Subject**</span></span> | <span data-ttu-id="0e10e-121">設定預設主體建立的事件。</span><span class="sxs-lookup"><span data-stu-id="0e10e-121">Set the default subject for events created.</span></span> <span data-ttu-id="0e10e-122">（256 個字元的最大）</span><span class="sxs-lookup"><span data-stu-id="0e10e-122">(256 character max)</span></span> |
    | <span data-ttu-id="0e10e-123">**必要出席者**</span><span class="sxs-lookup"><span data-stu-id="0e10e-123">**Required Attendees**</span></span> | <span data-ttu-id="0e10e-124">輸入以分隔您所需的預設出席者電子郵件地址 ';'。</span><span class="sxs-lookup"><span data-stu-id="0e10e-124">Enter your default required attendees email addresses separated by ';'.</span></span> <span data-ttu-id="0e10e-125">（256 個字元的最大）</span><span class="sxs-lookup"><span data-stu-id="0e10e-125">(256 character max)</span></span> |
    | <span data-ttu-id="0e10e-126">**選擇性出席者**</span><span class="sxs-lookup"><span data-stu-id="0e10e-126">**Optional Attendees**</span></span> | <span data-ttu-id="0e10e-127">輸入的預設的選擇性出席者電子郵件以分隔的地址 ';'。</span><span class="sxs-lookup"><span data-stu-id="0e10e-127">Enter your default optional attendees email addresses separated by ';'.</span></span> <span data-ttu-id="0e10e-128">（256 個字元的最大）</span><span class="sxs-lookup"><span data-stu-id="0e10e-128">(256 character max)</span></span> |

6. <span data-ttu-id="0e10e-129">選取行事曆：</span><span class="sxs-lookup"><span data-stu-id="0e10e-129">Select a calendar:</span></span> 

    ![Office365 行事曆](../core/media/office365-calendars.png)

    <span data-ttu-id="0e10e-131">完成時，您的屬性看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="0e10e-131">When finished, your properties look similar to the following:</span></span>

    ![端點屬性](../core/media/office365-calendar-send-properties.png)

7. <span data-ttu-id="0e10e-133">選取  **Ok**以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="0e10e-133">Select **Ok** to save your changes.</span></span>

### <a name="test-your-send-port"></a><span data-ttu-id="0e10e-134">測試您的傳送埠</span><span class="sxs-lookup"><span data-stu-id="0e10e-134">Test your send port</span></span>

<span data-ttu-id="0e10e-135">您可以使用簡單檔案接收埠和位置來建立 Office 365 Outlook 行事曆的事件。</span><span class="sxs-lookup"><span data-stu-id="0e10e-135">You can use a simple File receive port and location to create an event on your Office 365 Outlook Calendar.</span></span>

1. <span data-ttu-id="0e10e-136">建立使用 File 配接器的接收埠。</span><span class="sxs-lookup"><span data-stu-id="0e10e-136">Create a receive port using the File adapter.</span></span> <span data-ttu-id="0e10e-137">內您接收位置，設定**接收資料夾**至 \**C:\Temp\In\**，並將檔案遮罩設定為 **\*.xml**。</span><span class="sxs-lookup"><span data-stu-id="0e10e-137">Within your receive location,  set the **Receive folder** to \**C:\Temp\In\**, and set the file mask to **\*.xml**.</span></span>
2. <span data-ttu-id="0e10e-138">在您的 Office 365 Outlook 行事曆配接器會將傳送埠屬性，設定**篩選條件**至`BTS.ReceivePortName == <Receive Port Name>`。</span><span class="sxs-lookup"><span data-stu-id="0e10e-138">In your Office 365 Outlook Calendar adapter send port properties, set the **Filters** to `BTS.ReceivePortName == <Receive Port Name>`.</span></span>
3. <span data-ttu-id="0e10e-139">將下列內容貼入文字編輯器，並將檔案儲存為**Office365Calendar.xml**。</span><span class="sxs-lookup"><span data-stu-id="0e10e-139">Paste the following into a text editor, and save the file as **Office365Calendar.xml**.</span></span> <span data-ttu-id="0e10e-140">這是您的範例訊息。</span><span class="sxs-lookup"><span data-stu-id="0e10e-140">This is your sample message.</span></span>

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
    <span data-ttu-id="0e10e-141">**在 < BizTalk 安裝 Folder\SDK\Schemas > SDK 的一部分提供的 XML 結構描述**</span><span class="sxs-lookup"><span data-stu-id="0e10e-141">**The XML schema is provided as part of the SDK inside < BizTalk Installation Folder\SDK\Schemas >**</span></span>

4. <span data-ttu-id="0e10e-142">啟動檔案接收位置和 Office 365 Outlook 行事曆配接器傳送埠。</span><span class="sxs-lookup"><span data-stu-id="0e10e-142">Start the File receive location and the Office 365 Outlook Calendar adapter send port.</span></span>
5. <span data-ttu-id="0e10e-143">複製**Office365Calendar.xml**範例訊息至接收資料夾 (C:\Temp\In\)。</span><span class="sxs-lookup"><span data-stu-id="0e10e-143">Copy **Office365Calendar.xml** sample message into the receive folder (C:\Temp\In\).</span></span> <span data-ttu-id="0e10e-144">傳送埠會建立以 xml 為基礎的 Office 365 Outlook 行事曆中的事件。</span><span class="sxs-lookup"><span data-stu-id="0e10e-144">The send port creates an event in your Office 365 Outlook calendar based on the xml.</span></span>

## <a name="receive-events-using-a-receive-port"></a><span data-ttu-id="0e10e-145">使用 接收埠接收事件</span><span class="sxs-lookup"><span data-stu-id="0e10e-145">Receive events using a receive port</span></span>

1. <span data-ttu-id="0e10e-146">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**接收連接埠**，選取**新增**，然後選取**單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="0e10e-146">In the BizTalk Server Administration console, right-click **Receive Ports**, select **New**, and select **One-Way receive port**.</span></span>

    <span data-ttu-id="0e10e-147">[建立接收埠](../core/how-to-create-a-receive-port.md)提供一些指引。</span><span class="sxs-lookup"><span data-stu-id="0e10e-147">[Create a receive port](../core/how-to-create-a-receive-port.md) provides some guidance.</span></span>

2. <span data-ttu-id="0e10e-148">輸入名稱，然後選取**接收位置**。</span><span class="sxs-lookup"><span data-stu-id="0e10e-148">Enter a name, and select **Receive Locations**.</span></span>

3. <span data-ttu-id="0e10e-149">選取 **的新**，並**名稱**接收位置。</span><span class="sxs-lookup"><span data-stu-id="0e10e-149">Select **New**, and **Name** the receive location.</span></span> <span data-ttu-id="0e10e-150">在 **傳輸**，選取**Office 365 Outlook 行事曆**從**型別**下拉式清單，然後選取**設定**。</span><span class="sxs-lookup"><span data-stu-id="0e10e-150">In **Transport**, select **Office 365 Outlook Calendar** from the **Type** drop-down list, and then select **Configure**.</span></span>

4. <span data-ttu-id="0e10e-151">選取**登入...**，並登入您的 Office 365 帳戶。</span><span class="sxs-lookup"><span data-stu-id="0e10e-151">Select **Sign in …**, and sign in to your Office 365 Account.</span></span> <span data-ttu-id="0e10e-152">此帳戶是自動填入您的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="0e10e-152">The account is auto-populated with your email address.</span></span>

5. <span data-ttu-id="0e10e-153">允許 BizTalk Server 的存取權限的核准：</span><span class="sxs-lookup"><span data-stu-id="0e10e-153">Allow BizTalk Server approval for permission to access:</span></span>

    ![Office 365 行事曆權限](../core/media/office365-calendar-permissions.png)

6. <span data-ttu-id="0e10e-155">設定**端點**屬性：</span><span class="sxs-lookup"><span data-stu-id="0e10e-155">Configure the **Endpoint** properties:</span></span>

    |<span data-ttu-id="0e10e-156">使用</span><span class="sxs-lookup"><span data-stu-id="0e10e-156">Use this</span></span>|<span data-ttu-id="0e10e-157">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="0e10e-157">To do this</span></span>|  
    |---|---|  
    | <span data-ttu-id="0e10e-158">**行事曆**</span><span class="sxs-lookup"><span data-stu-id="0e10e-158">**Calendar**</span></span> | <span data-ttu-id="0e10e-159">選取會從中提取事件的行事曆。</span><span class="sxs-lookup"><span data-stu-id="0e10e-159">Select the calendar from which events will be fetched.</span></span>  |
    | <span data-ttu-id="0e10e-160">**正在啟動中**</span><span class="sxs-lookup"><span data-stu-id="0e10e-160">**Starting within**</span></span> | <span data-ttu-id="0e10e-161">選取在其中行事曆事件必須以 （預設值為 15 分鐘） 的 biztalk 接收開始的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="0e10e-161">Select the time interval within which a calendar event has to start in order to be received by BizTalk (default is 15 minutes).</span></span>  |

7. <span data-ttu-id="0e10e-162">選取行事曆：</span><span class="sxs-lookup"><span data-stu-id="0e10e-162">Selecting a calendar:</span></span>

    ![Office 365 行事曆](../core/media/office365-calendars.png)

    <span data-ttu-id="0e10e-164">完成時，您的屬性看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="0e10e-164">When finished, your properties look similar to the following:</span></span>

    ![端點屬性](../core/media/office365-calendar-receive-properties.png)

8. <span data-ttu-id="0e10e-166">選取  **Ok**以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="0e10e-166">Select **Ok** to save your changes.</span></span>

### <a name="test-your-receive-settings"></a><span data-ttu-id="0e10e-167">測試您接收設定</span><span class="sxs-lookup"><span data-stu-id="0e10e-167">Test your receive settings</span></span>

<span data-ttu-id="0e10e-168">您可以使用簡單的 File 傳送埠以接收來自您 Office 365 Outlook 行事曆的訊息。</span><span class="sxs-lookup"><span data-stu-id="0e10e-168">You can use a simple File send port to receive messages from your Office 365 Outlook Calendar.</span></span>

1. <span data-ttu-id="0e10e-169">建立使用 File 配接器的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="0e10e-169">Create a send port using the File adapter.</span></span> <span data-ttu-id="0e10e-170">在您傳送連接埠的屬性，設定**目的地資料夾**至 **C:\Temp\Out\**，並設定和**檔案名稱**至 **%MessageID%.xml**.</span><span class="sxs-lookup"><span data-stu-id="0e10e-170">Within your send port properties, set the **Destination folder** to **C:\Temp\Out\**, and set the and **File name** to **%MessageID%.xml**.</span></span>
2. <span data-ttu-id="0e10e-171">在您的檔案傳送埠屬性，設定**篩選條件**至`BTS.ReceivePortName == <Receive Port Name>`。</span><span class="sxs-lookup"><span data-stu-id="0e10e-171">In your File send port properties, set the **Filters** to  `BTS.ReceivePortName == <Receive Port Name>`.</span></span>
3. <span data-ttu-id="0e10e-172">開始 Office 365 Outlook 行事曆接收位置和 File 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="0e10e-172">Start the Office 365 Outlook Calendar receive location and the File send port.</span></span>
4. <span data-ttu-id="0e10e-173">尋找目的地資料夾 (c:\temp\out) 中的訊息。</span><span class="sxs-lookup"><span data-stu-id="0e10e-173">Look for messages in the destination folder (c:\temp\out).</span></span> 
<span data-ttu-id="0e10e-174">**在 SDK 所包含的 XML 結構描述`\Program Files (x86)\Microsoft BizTalk Server <your version>\SDK\Schemas`。**</span><span class="sxs-lookup"><span data-stu-id="0e10e-174">**The XML schema is included in the SDK at `\Program Files (x86)\Microsoft BizTalk Server <your version>\SDK\Schemas`.**</span></span>

### <a name="example-of-a-received-calendar-event-xml"></a><span data-ttu-id="0e10e-175">已接收的行事曆事件 xml 的範例</span><span class="sxs-lookup"><span data-stu-id="0e10e-175">Example of a received calendar event xml</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="0e10e-176">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="0e10e-176">Next steps</span></span>
<span data-ttu-id="0e10e-177">查看所有[Office 365 介面卡](office365-adapters.md)，或安裝[功能組件 3](https://aka.ms/bts2016fp3)。</span><span class="sxs-lookup"><span data-stu-id="0e10e-177">See all the [Office 365 adapters](office365-adapters.md), or install [Feature Pack 3](https://aka.ms/bts2016fp3).</span></span>