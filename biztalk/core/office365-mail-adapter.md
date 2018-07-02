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
# <a name="send-and-receive-email-with-office-365-outlook-email-adapter---biztalk-server"></a>傳送和接收電子郵件使用 Office 365 Outlook 電子郵件配接器的 BizTalk Server

Office 365 Outlook 電子郵件配接器可讓您傳送和接收來自 BizTalk 您 Office 365 Outlook 電子郵件的郵件。

## <a name="send-mail-using-a-send-port"></a>使用傳送埠傳送郵件

1. 在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，選取**新增**，然後選取**靜態單向傳送埠**。

    [建立傳送埠](../core/how-to-create-a-send-port2.md)提供一些指引。

2. 請輸入**名稱**。 在**傳輸**，將**型別**來**Office 365 Outlook 電子郵件**，然後選取**設定**。

3. 選取**登入...**，並登入您的 Office 365 帳戶。 此帳戶是自動填入您的電子郵件地址。

4. 允許 BizTalk Server 的存取權限的核准：

    ![Office 365 電子郵件權限](../core/media/office365-mail-permissions.png)

5. 設定您 Office 365 Outlook 電子郵件的預設屬性：

    |使用|以進行此動作|  
    |---|---|  
    | **若要** | 指定您的預設為分隔的郵件地址 ';'（256 個字元的最大）|
    | **副本** | 指定分隔您預設 CC 郵件地址 ';'（256 個字元的最大）|
    | **主旨** | 提到您的預設郵件主旨。 （256 個字元的最大） |
    | **重要性** | 選取您的重要性的值。 下拉式清單中包含的值**低**， **Normal**並**高**與**一般**為預設值。 |

    完成時，您的屬性看起來如下所示：

    ![端點屬性](../core/media/office365-mail-send-properties.png)

6. 選取  **Ok**以儲存變更。

### <a name="important-details"></a>重要的詳細資料

1. 您可以只傳送純文字訊息使用的傳送配接器。
2. 預設屬性也可能使用升級的屬性會更新：

|屬性|升級的屬性|
|---|---|
| **若要** | OfficeMail.To |
| **副本** | OfficeMail.CC |
| **主旨** | OfficeMail.Subject |
| **重要性** | OfficeMail.Importance |

### <a name="test-your-send-port"></a>測試您的傳送埠

您可以使用簡單檔案接收埠和位置來將訊息傳送至您的 Office 365 Outlook 電子郵件。

1. 建立使用 File 配接器的接收埠。 內您接收位置，設定**接收資料夾**至 **C:\Temp\In\**，並將檔案遮罩設定為 **\*.xml**。
2. 在您的 Office 365 Outlook 電子郵件配接器傳送埠屬性，設定**篩選條件**至`BTS.ReceivePortName == <Receive Port Name>`。
3. 將下列內容貼入文字編輯器，並將檔案儲存為**Office365Mail.xml**。 這是您的範例訊息。

    ```xml
    <ns0:Root xmlns:ns0="http://BizTalk_Server_Project1.Schema1"> 
        <Record> 
            <Name>BizTalk User</Name> 
            <ID>001</ID> 
        </Record> 
    </ns0:Root> 
    ```

4. 啟動檔案接收位置和 Office 365 Outlook 電子郵件的配接器傳送埠。
5. 複製**Office365Mail.xml**範例訊息至接收資料夾 (C:\Temp\In\)。 傳送埠以郵件主體傳送 XML 檔案，Office 365 Outlook 電子郵件。

## <a name="receive-email-using-a-receive-port"></a>收到電子郵件使用接收埠

1. 在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**接收連接埠**，選取**新增**，然後選取**單向接收埠**。

    [建立接收埠](../core/how-to-create-a-receive-port.md)提供一些指引。

2. 輸入名稱，然後選取**接收位置**。

3. 選取 **的新**，並**名稱**接收位置。 在 **傳輸**，選取**Office 365 Outlook 電子郵件**從**型別**下拉式清單，然後選取**設定**。

4. 選取 **[登入...**，並登入您的 Office 365 帳戶。 此帳戶是自動填入您的電子郵件地址。

5. 允許 BizTalk Server 的存取權限的核准：

    ![Office 365 電子郵件權限](../core/media/office365-mail-permissions.png)

6. 設定**端點**屬性：

    |使用|以進行此動作|  
    |---|---|  
    | **資料夾** | 選取 [取得電子郵件] 資料夾。 預設資料夾是收件匣。 請注意資料夾不是遞迴的本質。 例如，電子郵件的子資料夾不擷取。 |
    | **從啟動** | 輸入從 Office 365 收到電子郵件的方式。 這個值表示 receivedTimeStamp 在 Office 365 Outlook 電子郵件。 不會收到輸入的值的較新的電子郵件。  |
    | **僅未讀的郵件** | 勾選這一讀取未閱讀的電子郵件。 保留未勾選狀態可讀取所有的電子郵件。 |
    | **後置動作** | 選取 電子郵件已讀取後要執行的後置動作。 **無**是預設值，且沒有任何作用之後由 BizTalk 收到電子郵件。 **標示為已讀取**所暗示，BizTalk 收到一封電子郵件之後，您信箱中的電子郵件標示為已讀取。 **刪除**所暗示，BizTalk 會收到一封電子郵件之後，會刪除您信箱中的電子郵件。 Post 動作會執行以最佳方式為基礎。|

    完成時，您的屬性看起來如下所示：

    ![端點屬性](../core/media/office365-mail-receive-properties.png)

7. 選取  **Ok**以儲存變更。

### <a name="test-your-receive-settings"></a>測試您接收設定

您可以使用簡單的 File 傳送埠以接收來自您 Office 365 Outlook 電子郵件訊息。

1. 建立使用 File 配接器的傳送埠。 在您傳送連接埠的屬性，設定**目的地資料夾**至 **C:\Temp\Out\**，並設定和**檔案名稱**至 **%MessageID%.xml**.
2. 在您的檔案傳送埠屬性，設定**篩選條件**至`BTS.ReceivePortName == <Receive Port Name>`。
3. 開始 Office 365 Outlook 電子郵件接收位置和 File 傳送埠。
4. 尋找目的地資料夾 (c:\temp\out) 中的訊息。

### <a name="promoted-properties-from-receive-pipeline"></a>從 接收管線的升級的屬性

根據預設，會升級接收管線的下列屬性：

|屬性名稱| 升級的屬性|
|---|---|
| **重要性** | OfficeMail.ReceivedMailImportance |
| **主旨** | OfficeMail.ReceivedMailSubject |
| **SenderName** | OfficeMail.SenderName |
| **地** | OfficeMail.SenderAddress |
| **HasAttachments**| OfficeMail.HasAttachments |

> [!NOTE]
> 只有電子郵件的本文內容會傳遞至訊息。

## <a name="next-steps"></a>後續的步驟
查看所有[Office 365 介面卡](office365-adapters.md)，或安裝[功能組件 3](https://aka.ms/bts2016fp3)。