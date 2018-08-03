---
title: 使用 Office 365 Outlook 電子郵件配接器 |Microsoft Docs
description: 傳送和接收 BizTalk Server 中使用 Office 365 Outlook 電子郵件配接器的電子郵件訊息。 若要這樣做，建立接收埠和傳送埠使用的電子郵件配接器，並使用範例訊息來測試您的連接埠。
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
ms.openlocfilehash: daea28056180b436f226fa32b6179bfb1e091f7a
ms.sourcegitcommit: e7609c319b64ec20bf215d17aa5ac4f9dcae52ec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36946158"
---
# <a name="send-and-receive-email-with-office-365-outlook-email-adapter---biztalk-server"></a><span data-ttu-id="44e26-104">傳送和接收電子郵件使用 Office 365 Outlook 電子郵件配接器的 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="44e26-104">Send and receive email with Office 365 Outlook Email adapter - BizTalk Server</span></span>

<span data-ttu-id="44e26-105">Office 365 Outlook 電子郵件配接器可讓您傳送和接收來自 BizTalk 您 Office 365 Outlook 電子郵件的郵件。</span><span class="sxs-lookup"><span data-stu-id="44e26-105">The Office 365 Outlook Email Adapter allows you to send and receive mails from your Office 365 Outlook Email from BizTalk.</span></span>

## <a name="send-mail-using-a-send-port"></a><span data-ttu-id="44e26-106">使用傳送埠傳送郵件</span><span class="sxs-lookup"><span data-stu-id="44e26-106">Send mail using a send port</span></span>

1. <span data-ttu-id="44e26-107">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，選取**新增**，然後選取**靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="44e26-107">In the BizTalk Server Administration console, right-click **Send Ports**, select **New**, and select **Static One-way send port**.</span></span>

    <span data-ttu-id="44e26-108">[建立傳送埠](../core/how-to-create-a-send-port2.md)提供一些指引。</span><span class="sxs-lookup"><span data-stu-id="44e26-108">[Create a Send Port](../core/how-to-create-a-send-port2.md) provides some guidance.</span></span>

2. <span data-ttu-id="44e26-109">請輸入**名稱**。</span><span class="sxs-lookup"><span data-stu-id="44e26-109">Enter a **Name**.</span></span> <span data-ttu-id="44e26-110">在**傳輸**，將**型別**來**Office 365 Outlook 電子郵件**，然後選取**設定**。</span><span class="sxs-lookup"><span data-stu-id="44e26-110">In **Transport**, set the **Type** to **Office 365 Outlook Email**, and select **Configure**.</span></span>

3. <span data-ttu-id="44e26-111">選取**登入...**，並登入您的 Office 365 帳戶。</span><span class="sxs-lookup"><span data-stu-id="44e26-111">Select **Sign in …**, and sign in to your Office 365 Account.</span></span> <span data-ttu-id="44e26-112">此帳戶是自動填入您的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="44e26-112">The account is auto-populated with your email address.</span></span>

4. <span data-ttu-id="44e26-113">允許 BizTalk Server 的存取權限的核准：</span><span class="sxs-lookup"><span data-stu-id="44e26-113">Allow BizTalk Server approval for permission to access:</span></span>

    ![Office 365 電子郵件權限](../core/media/office365-mail-permissions.png)

5. <span data-ttu-id="44e26-115">設定您 Office 365 Outlook 電子郵件的預設屬性：</span><span class="sxs-lookup"><span data-stu-id="44e26-115">Configure your Office 365 Outlook Email default properties:</span></span>

    |<span data-ttu-id="44e26-116">使用</span><span class="sxs-lookup"><span data-stu-id="44e26-116">Use this</span></span>|<span data-ttu-id="44e26-117">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="44e26-117">To do this</span></span>|  
    |---|---|  
    | <span data-ttu-id="44e26-118">**若要**</span><span class="sxs-lookup"><span data-stu-id="44e26-118">**To**</span></span> | <span data-ttu-id="44e26-119">指定您的預設為分隔的郵件地址 ';'（256 個字元的最大）</span><span class="sxs-lookup"><span data-stu-id="44e26-119">Specify your default To mail addresses separated by ';' (256 character max)</span></span>|
    | <span data-ttu-id="44e26-120">**副本**</span><span class="sxs-lookup"><span data-stu-id="44e26-120">**CC**</span></span> | <span data-ttu-id="44e26-121">指定分隔您預設 CC 郵件地址 ';'（256 個字元的最大）</span><span class="sxs-lookup"><span data-stu-id="44e26-121">Specify your default CC mail addresses separated by ';' (256 character max)</span></span>|
    | <span data-ttu-id="44e26-122">**主旨**</span><span class="sxs-lookup"><span data-stu-id="44e26-122">**Subject**</span></span> | <span data-ttu-id="44e26-123">提到您的預設郵件主旨。</span><span class="sxs-lookup"><span data-stu-id="44e26-123">Mention your default mail subject.</span></span> <span data-ttu-id="44e26-124">（256 個字元的最大）</span><span class="sxs-lookup"><span data-stu-id="44e26-124">(256 character max)</span></span> |
    | <span data-ttu-id="44e26-125">**重要性**</span><span class="sxs-lookup"><span data-stu-id="44e26-125">**Importance**</span></span> | <span data-ttu-id="44e26-126">選取您的重要性的值。</span><span class="sxs-lookup"><span data-stu-id="44e26-126">Select your value of Importance.</span></span> <span data-ttu-id="44e26-127">下拉式清單中包含的值**低**， **Normal**並**高**與**一般**為預設值。</span><span class="sxs-lookup"><span data-stu-id="44e26-127">Dropdown contains values **Low**, **Normal** and **High** with **Normal** being the default.</span></span> |

    <span data-ttu-id="44e26-128">完成時，您的屬性看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="44e26-128">When finished, your properties look similar to the following:</span></span>

    ![端點屬性](../core/media/office365-mail-send-properties.png)

6. <span data-ttu-id="44e26-130">選取  **Ok**以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="44e26-130">Select **Ok** to save your changes.</span></span>

### <a name="important-details"></a><span data-ttu-id="44e26-131">重要的詳細資料</span><span class="sxs-lookup"><span data-stu-id="44e26-131">Important details</span></span>

1. <span data-ttu-id="44e26-132">您可以只傳送純文字訊息使用的傳送配接器。</span><span class="sxs-lookup"><span data-stu-id="44e26-132">You can only send plain text messages using the send adapter.</span></span>
2. <span data-ttu-id="44e26-133">預設屬性也可能使用升級的屬性會更新：</span><span class="sxs-lookup"><span data-stu-id="44e26-133">The default properties may also be updated using promoted properties:</span></span>

|<span data-ttu-id="44e26-134">屬性</span><span class="sxs-lookup"><span data-stu-id="44e26-134">Property</span></span>|<span data-ttu-id="44e26-135">升級的屬性</span><span class="sxs-lookup"><span data-stu-id="44e26-135">Promoted property</span></span>|
|---|---|
| <span data-ttu-id="44e26-136">**若要**</span><span class="sxs-lookup"><span data-stu-id="44e26-136">**To**</span></span> | <span data-ttu-id="44e26-137">OfficeMail.To</span><span class="sxs-lookup"><span data-stu-id="44e26-137">OfficeMail.To</span></span> |
| <span data-ttu-id="44e26-138">**副本**</span><span class="sxs-lookup"><span data-stu-id="44e26-138">**CC**</span></span> | <span data-ttu-id="44e26-139">OfficeMail.CC</span><span class="sxs-lookup"><span data-stu-id="44e26-139">OfficeMail.CC</span></span> |
| <span data-ttu-id="44e26-140">**主旨**</span><span class="sxs-lookup"><span data-stu-id="44e26-140">**Subject**</span></span> | <span data-ttu-id="44e26-141">OfficeMail.Subject</span><span class="sxs-lookup"><span data-stu-id="44e26-141">OfficeMail.Subject</span></span> |
| <span data-ttu-id="44e26-142">**重要性**</span><span class="sxs-lookup"><span data-stu-id="44e26-142">**Importance**</span></span> | <span data-ttu-id="44e26-143">OfficeMail.Importance</span><span class="sxs-lookup"><span data-stu-id="44e26-143">OfficeMail.Importance</span></span> |

### <a name="test-your-send-port"></a><span data-ttu-id="44e26-144">測試您的傳送埠</span><span class="sxs-lookup"><span data-stu-id="44e26-144">Test your send port</span></span>

<span data-ttu-id="44e26-145">您可以使用簡單檔案接收埠和位置來將訊息傳送至您的 Office 365 Outlook 電子郵件。</span><span class="sxs-lookup"><span data-stu-id="44e26-145">You can use a simple File receive port and location to send messages to your Office 365 Outlook Email.</span></span>

1. <span data-ttu-id="44e26-146">建立使用 File 配接器的接收埠。</span><span class="sxs-lookup"><span data-stu-id="44e26-146">Create a receive port using the File adapter.</span></span> <span data-ttu-id="44e26-147">內您接收位置，設定**接收資料夾**至 \**C:\Temp\In\**，並將檔案遮罩設定為 **\*.xml**。</span><span class="sxs-lookup"><span data-stu-id="44e26-147">Within your receive location, set the **Receive folder** to \**C:\Temp\In\**, and set the file mask to **\*.xml**.</span></span>
2. <span data-ttu-id="44e26-148">在您的 Office 365 Outlook 電子郵件配接器傳送埠屬性，設定**篩選條件**至`BTS.ReceivePortName == <Receive Port Name>`。</span><span class="sxs-lookup"><span data-stu-id="44e26-148">In your Office 365 Outlook Email adapter send port properties, set the **Filters** to `BTS.ReceivePortName == <Receive Port Name>`.</span></span>
3. <span data-ttu-id="44e26-149">將下列內容貼入文字編輯器，並將檔案儲存為**Office365Mail.xml**。</span><span class="sxs-lookup"><span data-stu-id="44e26-149">Paste the following into a text editor, and save the file as **Office365Mail.xml**.</span></span> <span data-ttu-id="44e26-150">這是您的範例訊息。</span><span class="sxs-lookup"><span data-stu-id="44e26-150">This is your sample message.</span></span>

    ```xml
    <ns0:Root xmlns:ns0="http://BizTalk_Server_Project1.Schema1"> 
        <Record> 
            <Name>BizTalk User</Name> 
            <ID>001</ID> 
        </Record> 
    </ns0:Root> 
    ```

4. <span data-ttu-id="44e26-151">啟動檔案接收位置和 Office 365 Outlook 電子郵件的配接器傳送埠。</span><span class="sxs-lookup"><span data-stu-id="44e26-151">Start the File receive location and the Office 365 Outlook Email adapter send port.</span></span>
5. <span data-ttu-id="44e26-152">複製**Office365Mail.xml**範例訊息至接收資料夾 (C:\Temp\In\)。</span><span class="sxs-lookup"><span data-stu-id="44e26-152">Copy **Office365Mail.xml** sample message into the receive folder (C:\Temp\In\).</span></span> <span data-ttu-id="44e26-153">傳送埠以郵件主體傳送 XML 檔案，Office 365 Outlook 電子郵件。</span><span class="sxs-lookup"><span data-stu-id="44e26-153">The send port sends the XML file as mail body to your Office 365 Outlook Email.</span></span>

## <a name="receive-email-using-a-receive-port"></a><span data-ttu-id="44e26-154">收到電子郵件使用接收埠</span><span class="sxs-lookup"><span data-stu-id="44e26-154">Receive email using a receive port</span></span>

1. <span data-ttu-id="44e26-155">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**接收連接埠**，選取**新增**，然後選取**單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="44e26-155">In the BizTalk Server Administration console, right-click **Receive Ports**, select **New**, and select **One-Way receive port**.</span></span>

    <span data-ttu-id="44e26-156">[建立接收埠](../core/how-to-create-a-receive-port.md)提供一些指引。</span><span class="sxs-lookup"><span data-stu-id="44e26-156">[Create a receive port](../core/how-to-create-a-receive-port.md) provides some guidance.</span></span>

2. <span data-ttu-id="44e26-157">輸入名稱，然後選取**接收位置**。</span><span class="sxs-lookup"><span data-stu-id="44e26-157">Enter a name, and select **Receive Locations**.</span></span>

3. <span data-ttu-id="44e26-158">選取 **的新**，並**名稱**接收位置。</span><span class="sxs-lookup"><span data-stu-id="44e26-158">Select **New**, and **Name** the receive location.</span></span> <span data-ttu-id="44e26-159">在 **傳輸**，選取**Office 365 Outlook 電子郵件**從**型別**下拉式清單，然後選取**設定**。</span><span class="sxs-lookup"><span data-stu-id="44e26-159">In **Transport**, select **Office 365 Outlook Email** from the **Type** drop-down list, and then select **Configure**.</span></span>

4. <span data-ttu-id="44e26-160">選取 **[登入...**，並登入您的 Office 365 帳戶。</span><span class="sxs-lookup"><span data-stu-id="44e26-160">Select **[Sign in …**, and sign in to your Office 365 Account.</span></span> <span data-ttu-id="44e26-161">此帳戶是自動填入您的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="44e26-161">The account is auto-populated with your email address.</span></span>

5. <span data-ttu-id="44e26-162">允許 BizTalk Server 的存取權限的核准：</span><span class="sxs-lookup"><span data-stu-id="44e26-162">Allow BizTalk Server approval for permission to access:</span></span>

    ![Office 365 電子郵件權限](../core/media/office365-mail-permissions.png)

6. <span data-ttu-id="44e26-164">設定**端點**屬性：</span><span class="sxs-lookup"><span data-stu-id="44e26-164">Configure the **Endpoint** properties:</span></span>

    |<span data-ttu-id="44e26-165">使用</span><span class="sxs-lookup"><span data-stu-id="44e26-165">Use this</span></span>|<span data-ttu-id="44e26-166">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="44e26-166">To do this</span></span>|  
    |---|---|  
    | <span data-ttu-id="44e26-167">**資料夾**</span><span class="sxs-lookup"><span data-stu-id="44e26-167">**Folder**</span></span> | <span data-ttu-id="44e26-168">選取 [取得電子郵件] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="44e26-168">Select the folder to get email.</span></span> <span data-ttu-id="44e26-169">預設資料夾是收件匣。</span><span class="sxs-lookup"><span data-stu-id="44e26-169">The default folder is Inbox.</span></span> <span data-ttu-id="44e26-170">請注意資料夾不是遞迴的本質。</span><span class="sxs-lookup"><span data-stu-id="44e26-170">Note that folders aren’t recursive in nature.</span></span> <span data-ttu-id="44e26-171">例如，電子郵件的子資料夾不擷取。</span><span class="sxs-lookup"><span data-stu-id="44e26-171">For example, email from subfolders aren’t retreived.</span></span> |
    | <span data-ttu-id="44e26-172">**從啟動**</span><span class="sxs-lookup"><span data-stu-id="44e26-172">**Start from**</span></span> | <span data-ttu-id="44e26-173">輸入從 Office 365 收到電子郵件的方式。</span><span class="sxs-lookup"><span data-stu-id="44e26-173">Enter how email is received from Office 365.</span></span> <span data-ttu-id="44e26-174">這個值表示 receivedTimeStamp 在 Office 365 Outlook 電子郵件。</span><span class="sxs-lookup"><span data-stu-id="44e26-174">This value indicates receivedTimeStamp of an email in Office 365 Outlook.</span></span> <span data-ttu-id="44e26-175">不會收到輸入的值的較新的電子郵件。</span><span class="sxs-lookup"><span data-stu-id="44e26-175">Email more recent than the entered values are received.</span></span>  |
    | <span data-ttu-id="44e26-176">**僅未讀的郵件**</span><span class="sxs-lookup"><span data-stu-id="44e26-176">**Unread mails only**</span></span> | <span data-ttu-id="44e26-177">勾選這一讀取未閱讀的電子郵件。</span><span class="sxs-lookup"><span data-stu-id="44e26-177">Check this to read only unread email.</span></span> <span data-ttu-id="44e26-178">保留未勾選狀態可讀取所有的電子郵件。</span><span class="sxs-lookup"><span data-stu-id="44e26-178">Keep it unchecked to read all email.</span></span> |
    | <span data-ttu-id="44e26-179">**後置動作**</span><span class="sxs-lookup"><span data-stu-id="44e26-179">**Post Action**</span></span> | <span data-ttu-id="44e26-180">選取 電子郵件已讀取後要執行的後置動作。</span><span class="sxs-lookup"><span data-stu-id="44e26-180">Select a post action to be performed after an email is read.</span></span> <span data-ttu-id="44e26-181">**無**是預設值，且沒有任何作用之後由 BizTalk 收到電子郵件。</span><span class="sxs-lookup"><span data-stu-id="44e26-181">**None** is the default, and does nothing after email is received by BizTalk.</span></span> <span data-ttu-id="44e26-182">**標示為已讀取**所暗示，BizTalk 收到一封電子郵件之後，您信箱中的電子郵件標示為已讀取。</span><span class="sxs-lookup"><span data-stu-id="44e26-182">**Mark as read** implies, that after an email is received by BizTalk, the email in your mailbox is marked as read.</span></span> <span data-ttu-id="44e26-183">**刪除**所暗示，BizTalk 會收到一封電子郵件之後，會刪除您信箱中的電子郵件。</span><span class="sxs-lookup"><span data-stu-id="44e26-183">**Delete** implies, that after an email is received by BizTalk, the email in your mailbox is deleted.</span></span> <span data-ttu-id="44e26-184">Post 動作會執行以最佳方式為基礎。</span><span class="sxs-lookup"><span data-stu-id="44e26-184">Post actions are performed on a best-effort basis.</span></span>|

    <span data-ttu-id="44e26-185">完成時，您的屬性看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="44e26-185">When finished, your properties look similar to the following:</span></span>

    ![端點屬性](../core/media/office365-mail-receive-properties.png)

7. <span data-ttu-id="44e26-187">選取  **Ok**以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="44e26-187">Select **Ok** to save your changes.</span></span>

### <a name="test-your-receive-settings"></a><span data-ttu-id="44e26-188">測試您接收設定</span><span class="sxs-lookup"><span data-stu-id="44e26-188">Test your receive settings</span></span>

<span data-ttu-id="44e26-189">您可以使用簡單的 File 傳送埠以接收來自您 Office 365 Outlook 電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="44e26-189">You can use a simple File send port to receive messages from your Office 365 Outlook Email.</span></span>

1. <span data-ttu-id="44e26-190">建立使用 File 配接器的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="44e26-190">Create a send port using the File adapter.</span></span> <span data-ttu-id="44e26-191">在您傳送連接埠的屬性，設定**目的地資料夾**至 **C:\Temp\Out\**，並設定和**檔案名稱**至 **%MessageID%.xml**.</span><span class="sxs-lookup"><span data-stu-id="44e26-191">Within your send port properties, set the **Destination folder** to **C:\Temp\Out\**, and set the and **File name** to **%MessageID%.xml**.</span></span>
2. <span data-ttu-id="44e26-192">在您的檔案傳送埠屬性，設定**篩選條件**至`BTS.ReceivePortName == <Receive Port Name>`。</span><span class="sxs-lookup"><span data-stu-id="44e26-192">In your File send port properties, set the **Filters** to  `BTS.ReceivePortName == <Receive Port Name>`.</span></span>
3. <span data-ttu-id="44e26-193">開始 Office 365 Outlook 電子郵件接收位置和 File 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="44e26-193">Start the Office 365 Outlook Email receive location and the File send port.</span></span>
4. <span data-ttu-id="44e26-194">尋找目的地資料夾 (c:\temp\out) 中的訊息。</span><span class="sxs-lookup"><span data-stu-id="44e26-194">Look for messages in the destination folder (c:\temp\out).</span></span>

### <a name="promoted-properties-from-receive-pipeline"></a><span data-ttu-id="44e26-195">從 接收管線的升級的屬性</span><span class="sxs-lookup"><span data-stu-id="44e26-195">Promoted Properties from receive pipeline</span></span>

<span data-ttu-id="44e26-196">根據預設，會升級接收管線的下列屬性：</span><span class="sxs-lookup"><span data-stu-id="44e26-196">The following properties from the Receive Pipeline are promoted by default:</span></span>

|<span data-ttu-id="44e26-197">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="44e26-197">Property Name</span></span>| <span data-ttu-id="44e26-198">升級的屬性</span><span class="sxs-lookup"><span data-stu-id="44e26-198">Promoted Property</span></span>|
|---|---|
| <span data-ttu-id="44e26-199">**重要性**</span><span class="sxs-lookup"><span data-stu-id="44e26-199">**Importance**</span></span> | <span data-ttu-id="44e26-200">OfficeMail.ReceivedMailImportance</span><span class="sxs-lookup"><span data-stu-id="44e26-200">OfficeMail.ReceivedMailImportance</span></span> |
| <span data-ttu-id="44e26-201">**主旨**</span><span class="sxs-lookup"><span data-stu-id="44e26-201">**Subject**</span></span> | <span data-ttu-id="44e26-202">OfficeMail.ReceivedMailSubject</span><span class="sxs-lookup"><span data-stu-id="44e26-202">OfficeMail.ReceivedMailSubject</span></span> |
| <span data-ttu-id="44e26-203">**SenderName**</span><span class="sxs-lookup"><span data-stu-id="44e26-203">**SenderName**</span></span> | <span data-ttu-id="44e26-204">OfficeMail.SenderName</span><span class="sxs-lookup"><span data-stu-id="44e26-204">OfficeMail.SenderName</span></span> |
| <span data-ttu-id="44e26-205">**地**</span><span class="sxs-lookup"><span data-stu-id="44e26-205">**SenderAddress**</span></span> | <span data-ttu-id="44e26-206">OfficeMail.SenderAddress</span><span class="sxs-lookup"><span data-stu-id="44e26-206">OfficeMail.SenderAddress</span></span> |
| <span data-ttu-id="44e26-207">**HasAttachments**</span><span class="sxs-lookup"><span data-stu-id="44e26-207">**HasAttachments**</span></span>| <span data-ttu-id="44e26-208">OfficeMail.HasAttachments</span><span class="sxs-lookup"><span data-stu-id="44e26-208">OfficeMail.HasAttachments</span></span> |

> [!NOTE]
> <span data-ttu-id="44e26-209">只有電子郵件的本文內容會傳遞至訊息。</span><span class="sxs-lookup"><span data-stu-id="44e26-209">Only the body content of the Email is passed through to the message.</span></span>

## <a name="next-steps"></a><span data-ttu-id="44e26-210">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="44e26-210">Next steps</span></span>
<span data-ttu-id="44e26-211">查看所有[Office 365 介面卡](office365-adapters.md)，或安裝[功能組件 3](https://aka.ms/bts2016fp3)。</span><span class="sxs-lookup"><span data-stu-id="44e26-211">See all the [Office 365 adapters](office365-adapters.md), or install [Feature Pack 3](https://aka.ms/bts2016fp3).</span></span>