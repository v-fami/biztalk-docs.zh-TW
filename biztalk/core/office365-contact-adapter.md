---
title: 使用 Office 365 Outlook 連絡人配接器 |Microsoft Docs
description: 使用 BizTalk Server 中的 Office 365 Outlook 連絡人配接器傳送訊息。 若要這樣做，請建立傳送埠，使用 Outlook 配接器，並使用範例 XML 訊息在 Office 365 Outlook 帳戶中建立連絡人。
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
ms.openlocfilehash: da423cba141dffa8779c97cef521ade730a3c846
ms.sourcegitcommit: 53b16fe6c1b1707ecf233dbd05f780653eb19419
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50752678"
---
# <a name="create-a-contact-using-the-office-365-outlook-contact-adapter---biztalk-server"></a><span data-ttu-id="b297f-104">建立連絡人，使用 Office 365 Outlook 連絡人配接器的 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="b297f-104">Create a contact using the Office 365 Outlook Contact adapter - BizTalk Server</span></span>

<span data-ttu-id="b297f-105">使用 BizTalk Server 中的 Office 365 Outlook 連絡人配接器，可在您的 Office 365 Outlook 中建立的連絡人。</span><span class="sxs-lookup"><span data-stu-id="b297f-105">Use the Office 365 Outlook Contact adapter in BizTalk Server to create contacts in your Office 365 Outlook.</span></span>

## <a name="create-a-contact-using-a-send-port"></a><span data-ttu-id="b297f-106">建立連絡人，使用傳送埠</span><span class="sxs-lookup"><span data-stu-id="b297f-106">Create a contact using a send port</span></span>

1. <span data-ttu-id="b297f-107">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，選取**新增**，然後選取**靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="b297f-107">In the BizTalk Server Administration console, right-click **Send Ports**, select **New**, and select **Static One-way send port**.</span></span>

    <span data-ttu-id="b297f-108">[建立傳送埠](../core/how-to-create-a-send-port2.md)提供一些指引。</span><span class="sxs-lookup"><span data-stu-id="b297f-108">[Create a Send Port](../core/how-to-create-a-send-port2.md) provides some guidance.</span></span>

2. <span data-ttu-id="b297f-109">請輸入**名稱**。</span><span class="sxs-lookup"><span data-stu-id="b297f-109">Enter a **Name**.</span></span> <span data-ttu-id="b297f-110">在**傳輸**，將**型別**來**Office 365 Outlook 連絡人**，然後選取**設定**。</span><span class="sxs-lookup"><span data-stu-id="b297f-110">In **Transport**, set the **Type** to **Office 365 Outlook Contact**, and select **Configure**.</span></span>

3. <span data-ttu-id="b297f-111">選取**登入...**，並登入您的 Office 365 帳戶。</span><span class="sxs-lookup"><span data-stu-id="b297f-111">Select **Sign in …**, and sign in to your Office 365 Account.</span></span> <span data-ttu-id="b297f-112">此帳戶是自動填入您的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="b297f-112">The account is auto-populated with your email address.</span></span>

4. <span data-ttu-id="b297f-113">允許 BizTalk Server 的存取權限的核准：</span><span class="sxs-lookup"><span data-stu-id="b297f-113">Allow BizTalk Server approval for permission to access:</span></span>

    ![Office 365 連絡人權限](../core/media/office365-contact-permissions.png)

5. <span data-ttu-id="b297f-115">選取  **Ok**以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="b297f-115">Select **Ok** to save your changes.</span></span>

### <a name="test-the-send-port"></a><span data-ttu-id="b297f-116">測試 傳送埠</span><span class="sxs-lookup"><span data-stu-id="b297f-116">Test the send port</span></span>

<span data-ttu-id="b297f-117">您可以使用簡單檔案接收埠和位置來建立您的 Office 365 Outlook 連絡人介面卡上的事件。</span><span class="sxs-lookup"><span data-stu-id="b297f-117">You can use a simple File receive port and location to create an event on your Office 365 Outlook Contact adapter.</span></span>

1. <span data-ttu-id="b297f-118">建立使用 File 配接器的接收埠。</span><span class="sxs-lookup"><span data-stu-id="b297f-118">Create a receive port using the File adapter.</span></span> <span data-ttu-id="b297f-119">內您接收位置，設定**接收資料夾**要**c:\\Temp\\中\\**，並將檔案遮罩設定為 **\*.xml**.</span><span class="sxs-lookup"><span data-stu-id="b297f-119">Within your receive location,  set the **Receive folder** to **C:\\Temp\\In\\**, and set the file mask to **\*.xml**.</span></span>
2. <span data-ttu-id="b297f-120">在您的 Office 365 Outlook 連絡人配接器會將傳送埠屬性，設定**篩選條件**至`BTS.ReceivePortName == <Receive Port Name>`。</span><span class="sxs-lookup"><span data-stu-id="b297f-120">In your Office 365 Outlook Contact adapter send port properties, set the **Filters** to `BTS.ReceivePortName == <Receive Port Name>`.</span></span>
3. <span data-ttu-id="b297f-121">將下列內容貼入文字編輯器，並將檔案儲存為**Office365Contact.xml**。</span><span class="sxs-lookup"><span data-stu-id="b297f-121">Paste the following into a text editor, and save the file as **Office365Contact.xml**.</span></span> <span data-ttu-id="b297f-122">這是您的範例訊息。</span><span class="sxs-lookup"><span data-stu-id="b297f-122">This is your sample message.</span></span>

    ```xml
        <ns0:Contact xmlns:ns0="http://schemas.microsoft.com/BizTalk/Office365OutlookContacts/Send">
            <categories>categories_0</categories>
            <categories>categories_1</categories>
            <categories>categories_2</categories>
            <birthday>1999-05-31T13:20:00.000-05:00</birthday>
            <fileAs>fileAs_0</fileAs>
            <displayName>displayName_0</displayName>
            <givenName>givenName_0</givenName>
            <initials>initials_0</initials>
            <middleName>middleName_0</middleName>
            <nickName>nickName_0</nickName>
            <surname>surname_0</surname>
            <title>title_0</title>
            <yomiGivenName>yomiGivenName_0</yomiGivenName>
            <yomiSurname>yomiSurname_0</yomiSurname>
            <yomiCompanyName>yomiCompanyName_0</yomiCompanyName>
            <generation>generation_0</generation>
            <jobTitle>jobTitle_0</jobTitle>
            <companyName>companyName_0</companyName>
            <department>department_0</department>
            <officeLocation>officeLocation_0</officeLocation>
            <profession>profession_0</profession>
            <businessHomePage>businessHomePage_0</businessHomePage>
            <assistantName>assistantName_0</assistantName>
            <manager>manager_0</manager>
            <homePhones>homePhones_0</homePhones>
            <homePhones>homePhones_1</homePhones>
            <mobilePhone>mobilePhone_0</mobilePhone>
            <businessPhones>businessPhones_0</businessPhones>
            <businessPhones>businessPhones_1</businessPhones>
            <spouseName>spouseName_0</spouseName>
            <personalNotes>personalNotes_0</personalNotes>
            <children>children_0</children>
            <children>children_1</children>
            <children>children_2</children>
            <emailAddresses>
                <name>name_0</name>
                <address>address_0</address>
            </emailAddresses>
            <emailAddresses>
                <name>name_0</name>
                <address>address_0</address>
            </emailAddresses>
            <homeAddress>
                <city>city_0</city>
                <countryOrRegion>countryOrRegion_0</countryOrRegion>
                <postalCode>10000</postalCode>
                <state>state_0</state>
                <street>street_0</street>
            </homeAddress>
            <businessAddress>
                <city>city_0</city>
                <countryOrRegion>countryOrRegion_0</countryOrRegion>
                <postalCode>11111</postalCode>
                <state>state_0</state>
                <street>street_0</street>
            </businessAddress>
            <otherAddress>
                <city>city_0</city>
                <countryOrRegion>countryOrRegion_0</countryOrRegion>
                <postalCode>21222</postalCode>
                <state>state_0</state>
                <street>street_0</street>
            </otherAddress>
        </ns0:Contact>
    ```
    <span data-ttu-id="b297f-123">**內部 SDK 的一部分提供的 XML 結構描述 < BizTalk 安裝資料夾\\SDK\\結構描述 >**</span><span class="sxs-lookup"><span data-stu-id="b297f-123">**The XML schema is provided as part of the SDK inside < BizTalk Installation Folder\\SDK\\Schemas >**</span></span>

4. <span data-ttu-id="b297f-124">啟動檔案接收位置和 Office 365 Outlook 連絡人配接器傳送埠。</span><span class="sxs-lookup"><span data-stu-id="b297f-124">Start the File receive location and the Office 365 Outlook Contact adapter send port.</span></span>
5. <span data-ttu-id="b297f-125">複製**Office365Contact.xml**範例訊息至接收資料夾 (c:\\Temp\\在\\)。</span><span class="sxs-lookup"><span data-stu-id="b297f-125">Copy **Office365Contact.xml** sample message into the receive folder (C:\\Temp\\In\\).</span></span> <span data-ttu-id="b297f-126">傳送埠會在您以 xml 為基礎的 Office 365 Outlook 帳戶中建立連絡人。</span><span class="sxs-lookup"><span data-stu-id="b297f-126">The send port creates a contact in your Office 365 Outlook account based on the xml.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b297f-127">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b297f-127">Next steps</span></span>
<span data-ttu-id="b297f-128">查看所有[Office 365 介面卡](office365-adapters.md)，或安裝[功能組件 3](https://aka.ms/bts2016fp3)。</span><span class="sxs-lookup"><span data-stu-id="b297f-128">See all the [Office 365 adapters](office365-adapters.md), or install [Feature Pack 3](https://aka.ms/bts2016fp3).</span></span>