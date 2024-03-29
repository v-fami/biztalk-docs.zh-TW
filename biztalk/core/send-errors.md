---
title: 將錯誤傳送 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3cf61c82-ad48-4555-af53-fb841fd0f503
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 76aa238227877ab70328e585d5d12b8c428e9061
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983320"
---
# <a name="send-errors"></a>傳送錯誤
診斷及解決 WCF 傳送錯誤的資訊。  
  
## <a name="failed-to-generate-odx-file"></a>無法產生 ODX 檔案

|                 |                                   錯誤詳細資料                                    |
|-----------------|------------------------------------------------------------------------------------|
|  產品名稱   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| 產品版本 |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    事件識別碼     |                                         0                                          |
|  事件來源   |                                         0                                          |
|    元件    |                                         0                                          |
|  符號名稱  |                                         0                                          |
|  訊息文字   |                            無法產生 ODX 檔案                             |
  
### <a name="explanation"></a>說明  
 此錯誤表示在使用服務時發生錯誤。  
  
### <a name="user-action"></a>使用者動作  
 請檢查服務有沒有有效的 Web 方法，該中繼資料裝載 （如果您擁有的 WCF 服務時）。 否則，請連絡服務提供者。  
  
 如需有關如何使用 WCF 服務的詳細資訊，請參閱[考量時使用 WCF 服務使用 WCF 傳送配接器](../core/considerations-when-consuming-wcf-services-with-the-wcf-send-adapters.md)。
 
## <a name="response-message-body-was-not-read"></a>未讀取回應訊息內文
  
|                 |                                        錯誤詳細資料                                        |
|-----------------|---------------------------------------------------------------------------------------------|
|  產品名稱   |     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]      |
| 產品版本 |                 [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                  |
|    事件識別碼     |                                              0                                              |
|  事件來源   |                                              0                                              |
|    元件    |                                              0                                              |
|  符號名稱  |                                              0                                              |
|  訊息文字   | 未讀取回應訊息內文 （這可能表示連接已經關閉。） |
  
### <a name="explanation"></a>說明  
 回應訊息傳送回之前，可能會中斷用戶端的連線。  
  
### <a name="user-action"></a>使用者動作  
 請檢查用戶端連接性。 採取的步驟和動作的範圍取決於連接埠類型。   
如需詳細資訊，請參閱 <<c0> [ 工具和公用程式來使用，以進行疑難排解](../core/tools-and-utilities-to-use-for-troubleshooting.md)。