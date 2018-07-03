---
title: 開發使用 WCF 通道模型的 SAP 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF channel model, developing applications by using
ms.assetid: 1ce70c8b-5eeb-4585-97af-b0a7b4398dac
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e2bce6ad43b6efce111a2801ba7a5b44e73dce1a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013127"
---
# <a name="develop-sap-applications-using-the-wcf-channel-model"></a>開發使用 WCF 通道模型的 SAP 應用程式
您可以使用[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]通道模型使用[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]直接透過通道執行個體的 SAP 繫結傳送 XML 訊息。  
  
 透過使用強型別類別與 WCF 服務模型會公開的方法中使用 WCF 通道模型的優點之一是通道模型提供更精密地控制您執行 SAP 系統的作業。 為什麼？ WCF 通道模型中您可以直接控制您透過通道傳送訊息的內容。  
  
 透過 WCF 服務模型的 WCF 通道模型提供的另一個主要優點是對資料流的更完整支援。 使用 WCF 通道模型，您可以執行：  
  
- 您的程式碼與配接器之間交換的所有訊息資料流都處理訊息的節點。  
  
- 資料流處理的 SendIdoc 和 ReceiveIdoc 作業訊息節點值。  
  
  這是因為 WCF 通道模型中您直接控制如何在您傳送至配接器的訊息上提供訊息內文，以及您如何使用訊息本文上您從配接器接收的訊息。  
  
  相反地，配接器不提供支援的 WCF 服務模型中的串流。 因為在 WCF 服務模型中，WCF 執行階段序列化和還原序列化其 XML 與 managed 程式碼物件的表示法之間的訊息，會使用完整的記憶體中複本的每個您配接器與交換的訊息。  
  
  本主題中的各節說明如何執行作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]使用 WCF 通道模型。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [SAP 配接器使用 WCF 通道模型概觀](../../adapters-and-accelerators/adapter-sap/overview-of-the-wcf-channel-model-with-the-sap-adapter.md)  
  
-   [建立通道，使用 SAP](../../adapters-and-accelerators/adapter-sap/create-a-channel-using-sap.md)  
  
-   [使用 WCF 通道模型叫用 SAP 系統上的作業](../../adapters-and-accelerators/adapter-sap/invoke-operations-on-the-sap-system-using-the-wcf-channel-model.md)  
  
-   [從 SAP 系統接收輸入的作業，使用 WCF 通道模型](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md) 
  
-   [資料流中使用 WCF 通道模型的 SAP 的一般檔案 Idoc](../../adapters-and-accelerators/adapter-sap/stream-flat-file-idocs-in-sap-using-the-wcf-channel-model.md)