---
title: FileAct 配接器安全性架構 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5faeebd6-5287-4ac4-a1db-e3c055d323d2
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ed8352b788af12fd3c38f489e9ddb65d8375f2a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222790"
---
# <a name="fileact-adapter-security-architecture"></a>FileAct 配接器安全性架構
檔案傳輸和接收的安全性是使用 SNL 和 SAG 中固有的憑證和密碼編譯功能來實作。  管理憑證，以此類推，完全不 FileAct 配接器的範圍內。 只要相關聯的 SAG SNL/執行個體註冊 SWIFT 和 SNL/SAG 上正確安裝的軟體之 FileAct 服務時，配接器會設備透過 SNL Api。 FileAct 配接器一定會將設定為"Advanced"（最佳做法） FACryptoMode。  
  
> [!NOTE]
>  配接器，您可以建立個別的安全性內容時，每個傳送埠。  
  
## <a name="see-also"></a>另請參閱  
 [FileAct 配接器架構](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md)   
 [FileAct 配接器即時的端對端原型](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md)   
 [FileAct 配接器即時區域基本型別](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md)   
 [FileAct 配接器儲存與轉送](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md)   
 [FileAct 配接器檔案和傳輸識別碼](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md)   
 [FileAct 配接器支援資訊傳輸](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md)   
 [FileAct 配接器傳遞通知](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md)   
 [FileAct 配接器狀態監視](../../adapters-and-accelerators/fileact-interact/fileact-adapter-status-monitoring.md)