---
title: FileAct 配接器安全性架構 |Microsoft Docs
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
ms.openlocfilehash: be9997dca0a4b7a5c619848e4ed38cf9099bbc16
ms.sourcegitcommit: be6273d612669adfbb9dc9208aaae0a8437d4017
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2018
ms.locfileid: "52826374"
---
# <a name="fileact-adapter-security-architecture"></a>FileAct 配接器安全性架構
檔案傳輸和接收的安全性是使用 SNL 及 SAG 中具有憑證] 和 [密碼編譯功能來實作。  憑證、 等等的管理完全是 FileAct 配接器的範圍外。 只要 FileAct 服務 SWIFT 與註冊相關聯的 SNL/SAG 執行個體和 SNL/SAG，配接器上安裝正確的軟體會使用透過 SNL Api 的功能。 FileAct 配接器一定會設定為"Advanced"（最佳做法） FACryptoMode。  
  
> [!NOTE]
>  配接器，您可以建立個別的安全性內容時，每個傳送埠。  
  
## <a name="see-also"></a>另請參閱  
 [FileAct 配接器架構](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md)   
 [FileAct 配接器即時端對端原型](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md)   
 [FileAct 配接器即時本機原型](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md)   
 [FileAct 配接器儲存和轉寄](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md)   
 [FileAct 配接器檔案和傳輸識別](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md)   
 [FileAct 配接器支援資訊傳輸](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md)   
 [FileAct 配接器傳遞通知](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md)   
 [FileAct 配接器狀態監控](../../adapters-and-accelerators/fileact-interact/fileact-adapter-status-monitoring.md)
