---
title: 控制流程中 BizTalk Adapter for JD Edwards OneWorld |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connection pooling
- control flows
- apartment threading
- apartment threading, business functions
ms.assetid: 1ec865d0-2257-453b-9230-1f3787ebac38
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0fc5a8be6516b61c4049242952967ce939513e9c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22237974"
---
# <a name="control-flow-in-biztalk-adapter-for-jd-edwards-oneworld"></a>BizTalk Adapter for JD Edwards OneWorld 中的控制流程
本主題將討論設計階段和執行階段控制流程，在 Microsoft BizTalk Adapter for JD Edwards OneWorld。  
  
## <a name="design-time-flow"></a>設計階段流程  
 當配接器開啟時 (使用 [傳輸屬性] 對話方塊中的認證與系統資訊)，就會建立 JD Edwards OneWorld 的一或多個應用程式商務功能執行個體，並置入集區。 在配接器精靈中瀏覽命名空間時，就會出現商務功能清單。 按一下商務功能，就會顯示其邏輯方法與方法簽章。  
  
## <a name="run-time-flow"></a>執行階段流程  
 對每個執行緒建立 JD Edwards OneWorld 商務功能執行個體，並置入集區。 將方法呼叫提交至商務服務時，就會使用 JD Edwards OneWorld 應用程式商務功能來讀取該方法的中繼資料；不過如果已快取該方法的中繼資料，商務功能就會使用快取的資訊，然後針對適當方法進行呼叫。 在執行階段，系統會動態地建構 JD Edwards OneWorld 介面層。 方法是透過 BizTalk Adapter for JD Edwards OneWorld 支援叫用和資料轉換的介面層。  
  
 BizTalk Adapter for JD Edwards OneWorld 會對應 JD Edwards OneWorld 應用程式方法簽章的介面描述，允許 BizTalk Server 與這些介面描述互動。  
  
 配接器可採用下列一或多種形式來擴充應用程式中的功能，讓企業中的應用程式與 JD Edwards OneWorld 應用程式互動：  
  
-   原生資料格式  
  
-   程序  
  
-   方法  
  
-   訊息  
  
-   屬性  
  
-   應用程式介面  
  
 在執行階段，BizTalk Adapter for JD Edwards OneWorld 可為與 JD Edwards OneWorld 互動的用戶端應用程式建置應用程式介面描述。 配接器可視需要建立、刪除以及叫用商務物件，在應用程式中執行運算以及直接叫用方法。 針對 JD Edwards OneWorld 發出的所有呼叫，都是同步呼叫。 配接器會接收來自 BizTalk Server 的 XML 訊息，以 SOAP 信封括住訊息，然後將呼叫的資料從 SOAP 訊息轉換成 Java 類型。  
  
 回覆會依照類似的程序送回：  
  
1.  將 Java 類型轉換成 SOAP 訊息。  
  
2.  將 SOAP 訊息轉換成 XML 訊息。  
  
3.  將 XML 訊息提交至 BizTalk Server 以供進一步處理。  
  
### <a name="apartment-threading-of-business-functions"></a>商務功能的 Apartment 執行緒  
 JD Edwards OneWorld 商務功能與任何執行個體都只能在其建立或取得所在的執行緒上使用。 這稱為*apartment 執行緒*。 BizTalk Adapter for JD Edwards OneWorld 的連線共用架構可管理可用連線的集區。  
  
### <a name="connection-pooling"></a>連接共用  
 連線共用可讓與伺服器系統的連線保持開啟，並予以重複使用，而不是在每個呼叫後關閉，透過此方法來改善呼叫效能。 BizTalk Adapter for JD Edwards OneWorld 可讓您共用特定登入識別碼內的連線，但仍保持控制所有集區的連線總數。  
  
 任何的新商務功能執行個體都會使用其建立所在的執行緒，並在完成每項作業之後摧毀該執行個體。 商務功能的所有 JD Edwards OneWorld 呼叫都沒有狀態，不過在作業期間，配接器會確定是在正確的執行緒上使用該商務功能。  
  
## <a name="see-also"></a>另請參閱  
 [開發應用程式](../core/developing-applications3.md)   
 [規劃與架構](../core/planning-and-architecture17.md)