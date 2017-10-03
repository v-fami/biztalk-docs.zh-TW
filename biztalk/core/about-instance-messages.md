---
title: "關於執行個體訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de7fc3d3-57a7-4df9-b981-127e21941e22
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf956fb9f201697ac8c2b7da2135e469e03de55e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="about-instance-messages"></a>關於執行個體訊息
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送和接收執行個體訊息，每個執行個體訊息通常都代表一或多個商業文件 (例如訂單)。 執行個體訊息是由一或多個結構描述定義的訊息結構執行個體。 一個結構描述或是一組一起使用的結構描述會定義哪些內容可組成有效的執行個體訊息。 例如，訂單可能被定義為在其中有數個記錄，例如 ShipTo 記錄、BillTo 記錄、Items 記錄等等。 這些記錄的每一個都可以定義為包含自己的子記錄和欄位。 對應的結構描述定義這些記錄與欄位的可能內容，對應的執行個體訊息則包含實際的訂單，而這些訂單包含根據結構描述結構化的訂單資料。  
  
 雖然所有的訊息格式都會轉譯成 XML 這種特殊格式以供內部處理，BizTalk Server 仍可使用可延伸的各種格式來傳送和接收執行個體訊息。 特定的 XML 文件會使用一組定義明確的開始和結束標記，以階層方式排列以便將資料組織在訊息中，並決定某個資料項目結束和另一個資料項目開始的位置。 一或多個對應的 XML 結構描述會定義在其他標記中允許哪些標記、順序為何，因此可決定符合訊息的結構。  
  
 另一個廣泛的格式類別 (也稱為一般檔案格式) 則是舊有系統常使用的。 這些格式使用分隔符號 (例如定位元) 及固定長度欄位的組合，來決定某個資料項目結束和另一個資料項目開始的位置。  
  
 本節提供 BizTalk Server 經常處理的兩個訊息類型結構的概要簡介。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [XML 訊息的結構](../core/structure-of-an-xml-message.md)  
  
-   [一般檔案訊息的結構](../core/structure-of-a-flat-file-message.md)