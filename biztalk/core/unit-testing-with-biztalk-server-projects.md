---
title: 使用 BizTalk Server 專案執行單元測試 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2594f29-fc34-4dda-9316-2afd4e0056d7
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da7147f4c2500946fb97c47592a2a4a35d3dcf62
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26008119"
---
# <a name="unit-testing-with-biztalk-server-projects"></a>使用 BizTalk Server 專案執行單元測試
BizTalk Server 在引進了單元測試可在啟用的功能**部署**BizTalk 專案的屬性頁。 下列螢幕擷取畫面顯示存取專案設計工具中，當您以滑鼠右鍵按一下專案，然後按一下此專案設定**屬性**。  
  
 ![](../core/media/projectdesignerenableunittesting.gif "ProjectDesignerEnableUnitTesting")  
  
 **公開啟用單元測試專案屬性的專案設計工具中的 [部署] 索引標籤的螢幕擷取畫面。**  
  
 這項功能可讓您建立結構描述、對應和管線的單元測試。 本節中的主題提供一些使用單元測試功能的方法範例。 啟用此功能並重新建置專案後，就會從下列基底類別衍生成品類別以支援單元測試。  
  
|成品類型|基底類別|  
|-------------------|----------------|  
|結構描述|**Microsoft.BizTalk.TestTools.Schema.TestableSchemaBase**|  
|對應|**Microsoft.BizTalk.TestTools.Mapper.TestableMapBase**|  
|管線|**Microsoft.BizTalk.TestTools.Pipeline.TestablePipelineBase**|  
  
## <a name="in-this-section"></a>本節內容  
  
-   [使用單元測試的結構描述和對應的功能](../core/using-the-unit-testing-feature-with-schemas-and-maps.md)  
  
-   [使用單元測試功能搭配管線](../core/using-the-unit-testing-feature-with-pipelines.md)  
  
## <a name="related-sections"></a>相關章節  
 [使用單元測試 (Visual Studio)](http://go.microsoft.com/fwlink/?LinkId=128890)