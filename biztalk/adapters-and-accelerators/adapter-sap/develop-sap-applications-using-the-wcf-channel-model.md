---
title: 開發 SAP 應用程式使用 WCF 通道模型 |Microsoft 文件
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
ms.openlocfilehash: 13015cb042d26c946abfa3c99a4f67034b8d9708
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="develop-sap-applications-using-the-wcf-channel-model"></a>開發 SAP 應用程式使用 WCF 通道模型
您可以使用[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]使用通道模型[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]直接透過 SAP 繫結的通道執行個體傳送 XML 訊息。  
  
 使用 WCF 通道模型，透過使用強型別類別和方法的 WCF 服務模型會公開的其中一個優點是通道模型提供更細微的控制，透過您在 SAP 系統執行的作業。 為什麼？ WCF 通道模型中直接控制您透過通道傳送訊息的內容。  
  
 WCF 通道模型提供的 WCF 服務模型透過另一個主要優點是更廣泛支援資料流。 使用 WCF 通道模型，您可以執行：  
  
-   您的程式碼與配接器之間交換的所有訊息資料流都處理的訊息節點。  
  
-   資料流處理的 SendIdoc 和 ReceiveIdoc 作業訊息節點值。  
  
 這是因為 WCF 通道模型中您直接控制如何在您傳送至配接器的訊息上提供訊息內文和使用您從配接器接收的訊息上的訊息本文的方式。  
  
 相反地，配接器不提供支援的 WCF 服務模型中的資料流。 因為在 WCF 服務模型中，WCF 執行階段序列化和還原序列化的 XML 和 managed 程式碼的物件表示法之間的訊息，進行完整的記憶體中複本的每個您配接器與交換的訊息。  
  
 本主題中的各節說明如何執行作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]使用 WCF 通道模型。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [SAP 配接器的 WCF 通道模型概觀](../../adapters-and-accelerators/adapter-sap/overview-of-the-wcf-channel-model-with-the-sap-adapter.md)  
  
-   [建立使用 SAP 的通道](../../adapters-and-accelerators/adapter-sap/create-a-channel-using-sap.md)  
  
-   [叫用 SAP 系統上的作業使用的 WCF 通道模型](../../adapters-and-accelerators/adapter-sap/invoke-operations-on-the-sap-system-using-the-wcf-channel-model.md)  
  
-   [接收從 SAP 系統的輸入的作業使用的 WCF 通道模型](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md) 
  
-   [使用 WCF 通道模型的 SAP 中的資料流處理一般檔案 Idoc](../../adapters-and-accelerators/adapter-sap/stream-flat-file-idocs-in-sap-using-the-wcf-channel-model.md)