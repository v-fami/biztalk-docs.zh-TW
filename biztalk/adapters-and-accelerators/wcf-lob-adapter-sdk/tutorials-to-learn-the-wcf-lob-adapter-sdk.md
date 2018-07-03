---
title: 若要了解 WCF LOB 配接器 SDK 教學課程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 99002b01-da8a-483e-ada3-1ffbe9cd7357
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e98ba2cd875df0def595f55786990d64b9234288
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011055"
---
# <a name="tutorials-to-learn-the-wcf-lob-adapter-sdk"></a>若要了解 WCF LOB 配接器 SDK 教學課程
[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]教學課程包含有關如何使用資訊[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]開發功能豐富的企業配接器，以協助您在企業內部的企業應用程式整合。 藉由使用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，operations 主控台和您所公開的資料可供任何應用程式可以取用 WCF 繫結，包括[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  
  
 教學課程包含簡單的範例，專為一組預先定義的作業。 您不需要能夠完成這些教學課程的商務系統中實際的一行。 不過，在教學課程中提供詳細資料可以從了解中繼資料寫入輸出的處理常式和更新版本套用至您的配接器開發需求。  

> [!TIP]
> 已完成的 Echo 配接器的 BizTalk 安裝檔案隨附`\BizTalk Server\ASDK_x86\Program Files\WCF LOB Adapter SDK\Documents\Samples`或`\BizTalk Server\ASDK_x64\Program Files\WCF LOB Adapter SDK\Documents\Samples`。
  
 使用下列的教學課程來了解如何使用的重要部分[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]:  
  
- [教學課程 1： 開發 Echo 配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)。 提供建立配接器會公開從一組預先定義的方法做為各種商務系統的字串作業的逐步指示。 配接器會提供許多常見的處理常式中實作[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]包括搜尋、 瀏覽、 輸入和輸出作業。 在成功完成本教學課程時，您會有功能的介面卡。  
  
- [教學課程 2： 使用 Echo 配接器，從.NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md)。 若是使用 Echo 配接器開發中，提供逐步指示[教學課程 1： 開發 Echo 配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)從.NET 專案。 您會新增至新的專案中，配接器服務參考，並提供程式碼來測試 Echo 配接器的輸入和輸出作業。  
  
- [教學課程 3： 裝載 Echo 配接器在 IIS 中的](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-3-hosting-the-echo-adapter-in-iis.md)。 提供逐步指示，針對中裝載 Echo 配接器開發[教學課程 1： 開發 Echo 配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)在網際網路資訊服務 (IIS) 處理。 您也會建立簡單的用戶端應用程式來取用 EchoString 作業的裝載配接器使用 svcutil.exe （ServiceModel 中繼資料公用程式）。  
  
  這些教學課程提供結構化的方法，來了解一些重要功能[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 不需要知道已完成[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]或[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]。 不過，您將了解多個如果您了解配接器設計背後的概念，並了解如何在可促進配接器設計[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 如需詳細資訊，請參閱：  
  
- [一般的開發人員工作，針對 WCF LOB 配接器 SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/common-developer-tasks-for-the-wcf-lob-adapter-sdk.md)  
  
- [WCF LOB 配接器 SDK 的重要元件](../../adapters-and-accelerators/wcf-lob-adapter-sdk/key-components-of-the-wcf-lob-adapter-sdk.md)  
  
  這些教學課程之前，您應該檢閱中的需求[您開始教學課程之前](../../core/before-you-begin-the-tutorial.md)。  
  
 
## <a name="in-this-section"></a>本節內容  
  
-   [開始教學課程之前](../../core/before-you-begin-the-tutorial.md)  
  
-   [教學課程 1：開發 Echo 配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)  
  
-   [教學課程 2：從 .NET 使用 Echo 配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md)  
  
-   [教學課程 3：在 IIS 中裝載 Echo 配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-3-hosting-the-echo-adapter-in-iis.md)  
  
## <a name="see-also"></a>另請參閱  
 [開始使用 BizTalk Server](../../core/getting-started-with-biztalk-server.md)