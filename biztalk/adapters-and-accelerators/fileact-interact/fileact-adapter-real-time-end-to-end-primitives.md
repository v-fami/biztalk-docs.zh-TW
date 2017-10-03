---
title: "FileAct 配接器即時的端對端原型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8591120-7259-49cb-90ac-954d8be226ed
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c95e52d4fbd5ec0df8ee580583f429ffe9e0f08d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="fileact-adapter-real-time-end-to-end-primitives"></a>FileAct 配接器即時的端對端原型
SWIFTNet 原型是一組應用程式與 SWIFTNet 連結 (SNL) 之間交換的 XML 文件。 針對每個端對端基本，那里兩個基本項目 – 一個在用戶端 （或傳送） 端，在伺服器上的另一個版本 （或接收） 側邊。 這包含四個訊息總數： 放置檔案的基本類型、 取得檔案的基本類型和每個傳送傳遞通知。  
  
 下圖顯示 FileAct 端對端原型。  
  
 ![FileAct 端 &#45; 至 &#45; 端點基本型別](../../adapters-and-accelerators/fileact-interact/media/6e3520cc-9ec4-445c-9114-c7cb760c1068.gif "6e3520cc-9ec4-445c-9114-c7cb760c1068")  
  
## <a name="put-file"></a>將檔案放  
 應用程式初始化放置檔案將檔案傳送至另一個 SWIFTNet 使用者的檔案系統基本項目。 為端對端函式中，沒有用戶端和伺服器端將檔案基本型別。 這些一起合作完成檔案傳輸。  
  
 每個這類的共同作業會傳送到單一檔案。 可能會以平行方式執行多個放置檔案的基本類型。  
  
## <a name="get-file"></a>取得檔案  
 應用程式初始化取得檔案基本項目從另一個 SWIFTNet 使用者的檔案系統中擷取。 為端對端函式中，沒有用戶端和伺服器端取得檔案的原始物件。 這些一起合作完成檔案傳輸。  
  
 每個這類的共同作業會擷取單一檔案。 可能會以平行方式執行多個取得檔案的基本類型。  
  
## <a name="send-delivery-notification"></a>傳遞通知  
 每個將檔案和每個基本的取得檔案有選擇讓接收端會傳回傳遞通知相關的檔案傳輸的檔案要求的傳送端。 對於放置檔案的基本操作，要求訊息會包含傳遞通知的要求。  
  
 如果是取得檔案基本，回應訊息會包含傳遞通知的要求。  
  
 在任一情況下，（比方說，在上一步 office 系統），確認檔案已收到的完整 （使用其中一個要檢查傳送到達的狀態已完成的狀態基本型別），以及檔案已經適當地安全儲存後接收應用程式分別會執行傳遞通知傳回給傳送者傳遞正面確認基本項目。 為端對端函式，沒有用戶端和伺服器端傳遞通知基本項目。 這些一起合作完成檔案傳遞通知。  
  
 傳遞通知，需要服務設計工具來建立與強制寄件者和接收者的檔案之間的通訊協定。  
  
## <a name="see-also"></a>另請參閱  
 [FileAct 配接器架構](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md)   
 [FileAct 配接器即時區域基本型別](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md)   
 [FileAct 配接器儲存與轉送](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md)   
 [FileAct 配接器安全性架構](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md)   
 [FileAct 配接器檔案和傳輸識別碼](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md)   
 [FileAct 配接器支援資訊傳輸](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md)   
 [FileAct 配接器傳遞通知](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md)   
 [FileAct 配接器狀態監視](../../adapters-and-accelerators/fileact-interact/fileact-adapter-status-monitoring.md)