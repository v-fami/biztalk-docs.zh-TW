---
title: "單元測試 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c40e5b82-dbb2-4767-8286-88e2de4129f3
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d5f792adf73fb1e3791f0dfe6c8c5f60a3bb81e6
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="unit-testing"></a>單元測試
BizTalk Server 導入的單元測試功能，可在啟用**部署**BizTalk 專案的屬性頁。 下列螢幕擷取畫面顯示存取專案設計工具中，當您以滑鼠右鍵按一下專案，然後按一下此專案設定**屬性**。  
  
 ![](../core/media/projectdesignerenableunittesting.gif "ProjectDesignerEnableUnitTesting")  
  
 **公開啟用單元測試專案屬性的專案設計工具中的 [部署] 索引標籤的螢幕擷取畫面**  
  
 這項功能可讓您建立結構描述、對應和管線的單元測試。 BizTalk Server 文件中的主題提供使用單元測試功能時，某些方法範例。 啟用此功能並重新建置專案後，就會從下列基底類別衍生成品類別以支援單元測試。  
  
|成品類型|基底類別|  
|-------------------|----------------|  
|結構描述|**Microsoft.BizTalk.TestTools.Schema.TestableSchemaBase**|  
|對應|**Microsoft.BizTalk.TestTools.Mapper.TestableMapBase**|  
|管線|**Microsoft.BizTalk.TestTools.Pipeline.TestablePipelineBase**|  
  
 如需單元測試所導入的 BizTalk Server 功能的詳細資訊，請參閱 BizTalk Server 說明中的下列主題：  
  
-   [使用單元測試的結構描述和對應的功能](http://go.microsoft.com/fwlink/?LinkId=150482)(http://go.microsoft.com/fwlink/?LinkId=150482)。  
  
-   [使用單元測試功能搭配管線](http://go.microsoft.com/fwlink/?LinkId=150483)(http://go.microsoft.com/fwlink/?LinkId=150483)  
  
## <a name="see-also"></a>請參閱  
 [實作自動化的測試](../technical-guides/implementing-automated-testing.md)