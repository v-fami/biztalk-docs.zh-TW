---
title: "若要了解 WCF LOB Adapter SDK 的教學課程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99002b01-da8a-483e-ada3-1ffbe9cd7357
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3efc47a5df445e18e4a78a005c31791fe1f1fa24
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tutorials-to-learn-the-wcf-lob-adapter-sdk"></a>若要了解 WCF LOB Adapter SDK 的教學課程
[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]教學課程包含有關如何使用資訊[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]來開發豐富的功能列商務配接器，以幫助您企業內部的企業應用程式整合。 使用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]的操作和您所公開的資料可供任何應用程式可以取用 WCF 繫結，包括[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  
  
 教學課程包含簡單的範例，建立一組預先定義的作業。 您不需要完成這些教學課程的商務系統中實際的一行。 不過，在教學課程中提供詳細資料可以從了解中繼資料來寫入輸出的處理常式和更新版本套用至您的配接器開發需求。  

> [!TIP]
> 已完成的回應配接器隨附於 BizTalk 安裝檔案在`\BizTalk Server\ASDK_x86\Program Files\WCF LOB Adapter SDK\Documents\Samples`或`\BizTalk Server\ASDK_x64\Program Files\WCF LOB Adapter SDK\Documents\Samples`。
  
 使用下列的教學課程來了解如何使用的關鍵部分[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]:  
  
-   [教學課程 1： 在開發回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)。 提供建立會公開一組預先定義的方法做為商務系統的一行從字串作業的配接器的逐步指示。 配接器提供許多通用的處理常式中實作[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]包括搜尋、 瀏覽、 輸入和輸出作業。 在成功完成本教學課程之後，您會有功能的介面卡。  
  
-   [教學課程 2： 使用回應配接器從.NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md)。 提供逐步指示，針對以耗用回應配接器開發[教學課程 1： 開發回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)從.NET 專案。 您會將配接器服務參考加入新的專案，並提供程式碼來測試回應配接器的輸入和輸出作業。  
  
-   [教學課程 3： 裝載在 IIS 中的回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-3-hosting-the-echo-adapter-in-iis.md)。 提供逐步指示，以裝載回應配接器開發的[教學課程 1： 開發回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)網際網路資訊服務 (IIS) 中處理。 您也會建立簡單的用戶端應用程式使用託管的配接器的 EchoString 作業使用 svcutil.exe （ServiceModel 中繼資料公用程式）。  
  
 這些教學課程提供結構化的方法，以了解一些重要功能[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 可以使用沒有的知識來完成[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]或[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]。 不過，您將深入當您了解配接器設計背後的概念，並了解在配接器的設計透過的實現[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 如需詳細資訊，請參閱：  
  
-   [一般的開發人員工作，針對 WCF LOB 配接器 SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/common-developer-tasks-for-the-wcf-lob-adapter-sdk.md)  
  
-   [WCF LOB 配接器 SDK 的重要元件](../../adapters-and-accelerators/wcf-lob-adapter-sdk/key-components-of-the-wcf-lob-adapter-sdk.md)  
  
 在開始這些教學課程之前，您應該檢閱中的需求[開始教學課程之前](../../core/before-you-begin-the-tutorial.md)。  
  
 
## <a name="in-this-section"></a>本節內容  
  
-   [開始教學課程之前](../../core/before-you-begin-the-tutorial.md)  
  
-   [教學課程 1： 在開發回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)  
  
-   [教學課程 2： 使用回應配接器從.NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md)  
  
-   [教學課程 3： 裝載在 IIS 中的回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-3-hosting-the-echo-adapter-in-iis.md)  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 使用者入門](../../core/getting-started-with-biztalk-server.md)