---
title: 處理錯誤的錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 602be8a5-1f28-457d-8e12-ba06cff65491
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c494614465df4faeead9ec30d79dfdf47cc321c1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999079"
---
# <a name="error-handling-errors"></a>錯誤處理錯誤
診斷及解決 WCF 錯誤處理錯誤的資訊。  

## <a name="error-handling-options-disable-location-on-failure-and-suspend-request-message-on-failure-should-not-both-be-set-to-false"></a>錯誤處理選項 停用失敗的位置 」 和 「 擱置失敗的要求訊息 」 應該不能兩者都設定為 false    

|                 |                                                                                                詳細資料                                                                                                 |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                           |
| 產品版本 |                                                                       [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                                                       |
|    事件識別碼     |                                                                                                   0                                                                                                    |
|  事件來源   |                                                                                                   0                                                                                                    |
|    元件    |                                                                                                   0                                                                                                    |
|  符號名稱  |                                                                                                   0                                                                                                    |
|  訊息文字   | 錯誤處理選項 [停用失敗的位置] 並 「 暫停失敗要求訊息 」 應該不能兩者都設定為 false 因為可能會造成訊息遺失。 請將一個或兩個選項設定為 true |

## <a name="explanation"></a>說明  
 Wcf-netmsmq 配接器的選項中**停用失敗的位置**並**失敗時擱置要求訊息**應該不能兩者都選取。 因為接收位置會繼續接收無效的訊息，而這些訊息不會暫停，而且不會儲存在訊息方塊中，可能會造成訊息遺失。  

## <a name="user-action"></a>使用者動作  
 您可以使用下列程序來設定介面卡設定。    

1. 開啟 [BizTalk Server 管理] 。  

2. 在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。  

3. 找出您的應用程式，然後找出您的傳輸。  

4. 以滑鼠右鍵按一下傳輸名稱。  

5. 選取 **屬性**。  

6. 在 連接埠**型別**清單中，選取正確的連接埠。  

7. 選取 **[設定]**。  

8. 在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**對話方塊中，選取**訊息**] 索引標籤。  

9. 在 **錯誤處理**區段中，確定其中一個**停用失敗的位置**或**失敗時擱置要求訊息**已核取。
