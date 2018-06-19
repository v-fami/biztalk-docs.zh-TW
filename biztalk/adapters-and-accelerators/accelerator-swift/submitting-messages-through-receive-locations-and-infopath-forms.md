---
title: 提交訊息到接收位置和 InfoPath 表單 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, receive locations
- receive locations, messages
- messages, InfoPath forms
- InfoPath forms, messages
ms.assetid: e8676830-3fbc-423f-82f6-03e6a532075f
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4589649be79ce369f0e6756ae7f96615d4a36c0f
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26005119"
---
# <a name="submitting-messages-through-receive-locations-and-infopath-forms"></a>正在提交訊息到接收位置和 InfoPath 表單
接收位置接收訊息提交到[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]應用程式。 您可以定義為實體的端點來接收訊息，使用指定的傳輸通訊協定設定的接收位置。 例如，接收位置可能設定接收檔案放到 使用檔案傳輸特定的檔案系統資料夾。  
  
 您建立以邏輯方式分組和管理接收埠接收位置的接收位置。 針對每個接收位置，您會指定接收管線，並在該特定接收位置接收訊息的實際處理 （解碼、 解譯、 驗證，等等）。 A4SWIFT 繫結接收位置接收連接埠，以邏輯方式分組和管理接收位置。  
  
 若要提交 SWIFT 訊息透過接收位置的 A4SWIFT 應用程式，必須是卸除設定的接收位置、 使用 SWIFT 解譯器的接收管線處理、 剖析和驗證訊息 SWIFT 的解譯器，並發佈至 MessageBox 資料庫。 訊息發佈到 MessageBox 資料庫之後，A4SWIFT 應用程式中的其他元件就會擷取 （使用訂用帳戶） 訊息進行其他處理。 例如，您可以使用傳送埠的最後一個路由。  
  
 如需有關建立和設定接收埠和接收位置，請參閱 BizTalk Server 說明。  
  
 您也可以提交新的訊息，透過[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]形成，請使用 Message Repair 和 New Submission 功能。 若要這樣做，請您開啟[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單從 MRSR 網站中的資料夾，該訊息。 您在中的資料填入[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]形成、 您的憑證進行簽署，然後提交它。 Message Repair 和 New Submission 協調流程處理的訊息。  
  
## <a name="see-also"></a>請參閱  
 [BizTalk Accelerator for SWIFT 執行階段](../../adapters-and-accelerators/accelerator-swift/biztalk-accelerator-for-swift-runtime.md)