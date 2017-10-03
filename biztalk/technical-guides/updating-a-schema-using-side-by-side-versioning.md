---
title: "更新結構描述使用並存的版本設定 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7360ec5-b5e9-40c7-9a7c-965fcc95ddb0
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3d63b93f665e80f88e2d9e81b2337e7b198b3df
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="updating-a-schema-using-side-by-side-versioning"></a>更新結構描述中使用的並存版本控制
您可以執行的並存版本控制結構描述。 您可以藉由加入新的結構描述版本的組件，但保留現有的結構描述 （和其版本） 升級結構描述的版本保持不變。  
  
 如果要增加結構描述版本，您必須更新結構描述以取得任何管線執行個體並使用它的管線元件的參考。 您也必須更新參考結構描述 （或建立新的對應） 的對應，以及任何依賴該結構描述的協調流程。  
  
 如果您解除部署結構描述，舊版的結構描述中，如果有的話，會變成作用中。  
  
## <a name="schema-resolution-in-pipelines"></a>在管線中的結構描述解析  
 如果您將 BizTalk 群組中包含具有相同的訊息類型做為現有的結構描述的新結構描述的組件加入至應用程式，在管線中發生結構描述解析時將使用具有最新的版本號碼的結構描述。 如果一種訊息類型參考一個以上的.NET 型別，模稜兩可能導致管線執行失敗。 這是因為結構描述查閱會使用訊息類型、目標命名空間以及執行個體的根名稱。 這種失敗可能會發生在任何使用結構描述具有相同的訊息類型做為新的結構描述的應用程式管線。 如需結構描述解析的詳細資訊，請參閱[管線元件中的結構描述解析](http://go.microsoft.com/fwlink/?LinkID=154207)(http://go.microsoft.com/fwlink/?LinkID=154207) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
 XML 解譯器的結構描述解析行為可能會需要額外變更之後新增新版與舊版並存的結構描述。 在某些情況下，您可能想要在管線設計師 」 中的管線解譯器屬性結構描述的特定版本的硬式編碼參考。 這可讓您避免動態解析行為，在其中 XML 解譯器會決定使用訊息類型以動態方式載入的結構描述探索在執行階段從訊息 XML 內容。  
  
## <a name="updating-a-schema-in-an-orchestration"></a>更新協調流程中的結構描述  
 當您變更與多個傳送相關聯的結構描述，並接收圖形的協調流程中時，您可以更輕鬆地變更進行每次傳送相關聯之訊息的訊息類型屬性設定，或接收 圖形至多部分訊息類型，而非結構描述。 然後，您可以設定每個圖形是相同的結構描述相關聯的訊息部分的型別屬性。 如此一來，您可以透過隨後變更結構描述的變更類型屬性的每個訊息部分，而不必變更每個圖形的訊息類型。 如需這個程序方便變更的詳細資訊，請參閱[8 秘訣和訣竅更好的 BizTalk 程式設計](http://go.microsoft.com/fwlink/?LinkId=101594)白皮書 (http://go.microsoft.com/fwlink/?LinkId=101594)。  
  
## <a name="versioning-schemas"></a>管理結構描述版本  
 BizTalk Server 會從最新版本包含它的組件的結構描述。 這表示，如果您建立新的結構描述版本，新的版本會完全取代所有舊版的結構描述。 這在交易期間很短時是可行的。 不過，在商務程序管理解決方案中的交易期間較長： 訂單可能需要一年才能完成。  
  
 為了同時使用某個結構描述的多個版本，解決方案中的每個結構描述會在其命名空間中包含版本號碼。 BizTalk 管線會判斷目標命名空間為基礎的訊息加上結構描述中定義的根節點名稱的訊息類型。 例如，Order 結構描述的命名空間如下所示：  
  
```  
http://Microsoft.Samples.BizTalk.SouthridgeVideo.Schemas.Order.v1  
```  
  
 命名空間的結構描述和包含的版本號碼會識別唯一的結構描述的命名空間，因為新的結構描述將會從較舊的版本不同。 因此，可以不取代舊的結構描述，即可使用新的結構描述。  
  
 變更結構描述版本會影響您的方案，有許多組件，所以這必須事先規劃。 如需效果的結構描述版本變更，請參閱[管線元件中的結構描述解析](http://go.microsoft.com/fwlink/?LinkID=154207)(http://go.microsoft.com/fwlink/?LinkID=154207) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
 在變更協調流程中的結構描述的版本，請使用 多部分訊息類型。 這樣會導致更大的彈性時結構描述版本。 使用多部分訊息類型的優勢的相關資訊，請參閱 MSDN Magazine 文件中秘訣 #1，「 永遠使用多部分訊息類型，」 [8 秘訣和訣竅更好的 BizTalk 程式設計](http://go.microsoft.com/fwlink/?LinkId=101594)(http://go.microsoft.com/fwlink/？LinkId = 101594)。  
  
## <a name="see-also"></a>另請參閱  
 [更新應用程式的最佳作法](../technical-guides/best-practices-for-updating-applications.md)