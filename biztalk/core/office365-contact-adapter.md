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
ms.openlocfilehash: 3185e080be7a4222ac51072506eb9657eb7b1e1b
ms.sourcegitcommit: e7609c319b64ec20bf215d17aa5ac4f9dcae52ec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36946175"
---
# <a name="create-a-contact-using-the-office-365-outlook-contact-adapter---biztalk-server"></a>建立連絡人，使用 Office 365 Outlook 連絡人配接器的 BizTalk Server

使用 BizTalk Server 中的 Office 365 Outlook 連絡人配接器，可在您的 Office 365 Outlook 中建立的連絡人。

## <a name="create-a-contact-using-a-send-port"></a>建立連絡人，使用傳送埠

1. 在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，選取**新增**，然後選取**靜態單向傳送埠**。

    [建立傳送埠](../core/how-to-create-a-send-port2.md)提供一些指引。

2. 請輸入**名稱**。 在**傳輸**，將**型別**來**Office 365 Outlook 連絡人**，然後選取**設定**。

3. 選取**登入...**，並登入您的 Office 365 帳戶。 此帳戶是自動填入您的電子郵件地址。

4. 允許 BizTalk Server 的存取權限的核准：

    ![Office 365 連絡人權限](../core/media/office365-contact-permissions.png)

5. 選取  **Ok**以儲存變更。

### <a name="test-the-send-port"></a>測試 傳送埠

您可以使用簡單檔案接收埠和位置來建立您的 Office 365 Outlook 連絡人介面卡上的事件。

1. 建立使用 File 配接器的接收埠。 內您接收位置，設定**接收資料夾**至 **C:\Temp\In\**，並將檔案遮罩設定為 **\*.xml**。
2. 在您的 Office 365 Outlook 連絡人配接器會將傳送埠屬性，設定**篩選條件**至`BTS.ReceivePortName == <Receive Port Name>`。
3. 將下列內容貼入文字編輯器，並將檔案儲存為**Office365Contact.xml**。 這是您的範例訊息。

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
    **在 < BizTalk 安裝 Folder\SDK\Schemas > SDK 的一部分提供的 XML 結構描述**

4. 啟動檔案接收位置和 Office 365 Outlook 連絡人配接器傳送埠。
5. 複製**Office365Contact.xml**範例訊息至接收資料夾 (C:\Temp\In\)。 傳送埠會在您以 xml 為基礎的 Office 365 Outlook 帳戶中建立連絡人。

## <a name="next-steps"></a>後續的步驟
查看所有[Office 365 介面卡](office365-adapters.md)，或安裝[功能組件 3](https://aka.ms/bts2016fp3)。