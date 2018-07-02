---
title: 更新使用並排顯示版本設定結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a7360ec5-b5e9-40c7-9a7c-965fcc95ddb0
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed0d9d3a204641ac4bccb856e62be15cc2589786
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976407"
---
# <a name="updating-a-schema-using-side-by-side-versioning"></a>更新結構描述使用並排顯示版本設定
您可以執行使用結構描述的並排顯示版本控制。 您可以藉由加入組件的結構描述的新版本，同時保留現有的結構描述 （和其版本） 升級結構描述版本保持不變。  
  
 如果要增加的結構描述版本，您必須更新任何管線的執行個體並使用它的管線元件的結構描述的參考。 您也必須更新參考結構描述 （或建立新的對應） 的對應，以及任何依賴該結構描述的協調流程。  
  
 如果您解除部署結構描述，舊版的結構描述中，如果有的話，會變成作用中。  
  
## <a name="schema-resolution-in-pipelines"></a>在管線中的結構描述解析  
 如果您將 BizTalk 群組中包含具有相同的訊息類型做為現有的結構描述的新結構描述的組件加入至應用程式，在管線中的結構描述解析時將使用具有最新的版本號碼的結構描述。 如果一種訊息類型參考一個以上的.NET 型別，此模稜兩可可能會導致管線執行失敗。 這是因為結構描述查閱會使用訊息類型、目標命名空間以及執行個體的根名稱。 管線中使用的結構描述具有相同的訊息類型做為新的結構描述的任何應用程式可能會發生這種類型的失敗。 如需有關結構描述解析的詳細資訊，請參閱 <<c0> [ 管線元件中的結構描述解析](http://go.microsoft.com/fwlink/?LinkID=154207)(<http://go.microsoft.com/fwlink/?LinkID=154207>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
 新增新版與舊版並存的結構描述之後，XML 解譯器的結構描述解析行為可能需要額外的變更。 在某些情況下，您可能想要在管線設計師 」 中的管線解譯器屬性結構描述的特定版本的硬式編碼參考。 這可讓您避免動態解析行為，以 XML 解譯器會決定要以動態方式使用訊息類型載入結構描述在執行階段從訊息 XML 內容探索。  
  
## <a name="updating-a-schema-in-an-orchestration"></a>更新協調流程中的結構描述  
 當您變更與多個傳送相關聯的結構描述，並在協調流程接收圖形時，您可以變更容易藉由設定每次傳送相關聯訊息的訊息類型屬性，或接收圖形的多部分訊息類型，而非結構描述。 然後，您可以設定為相同的結構描述的每個圖形相關聯的訊息部分的型別屬性。 如此一來，您可以隨後變更結構描述所變更的每個訊息部分的 [類型] 屬性，而不需要變更每個圖形的訊息類型。 如需此程序輕鬆變更的詳細資訊，請參閱[8 的祕訣和訣竅更好 BizTalk 程式設計](http://go.microsoft.com/fwlink/?LinkId=101594)（英文） 白皮書 (http://go.microsoft.com/fwlink/?LinkId=101594)。  
  
## <a name="versioning-schemas"></a>管理結構描述版本  
 BizTalk Server 會從包含它的組件的最新版本的結構描述。 這表示，如果您建立結構描述的新版本時，新的版本會完全取代結構描述的所有先前的版本。 這在交易期間很短時是可行的。 不過，在商務程序管理解決方案中的交易都是長時間執行： 訂單可能需要一年才能完成。  
  
 為了同時使用某個結構描述的多個版本，解決方案中的每個結構描述會在其命名空間中包含版本號碼。 BizTalk 管線會判斷目標命名空間為基礎的訊息加上結構描述中定義的根節點名稱的訊息類型。 例如，Order 結構描述的命名空間如下所示：  
  
```  
http://Microsoft.Samples.BizTalk.SouthridgeVideo.Schemas.Order.v1  
```  
  
 命名空間的結構描述和包含的版本號碼可讓識別唯一的結構描述的命名空間，因為新的結構描述會從舊的版本不同。 因此，可以不取代舊的結構描述，即可使用新的結構描述。  
  
 變更結構描述版本會影響您的方案中的許多部分，因此這應該事先規劃。 如需效果的結構描述版本變更，請參閱[管線元件中的結構描述解析](http://go.microsoft.com/fwlink/?LinkID=154207)(<http://go.microsoft.com/fwlink/?LinkID=154207>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
 在變更協調流程中的結構描述版本，請使用 多部分訊息類型。 這樣會導致更大的彈性時結構描述版本。 使用多部分訊息類型的優勢的相關資訊，請參閱秘訣 #1，< 一律使用多部分訊息類型 」，在 MSDN magazine 》 文章[8 的祕訣和訣竅更好的 BizTalk 程式設計](http://go.microsoft.com/fwlink/?LinkId=101594)(http://go.microsoft.com/fwlink/?LinkId=101594)。  
  
## <a name="see-also"></a>另請參閱  
 [更新應用程式的最佳做法](../technical-guides/best-practices-for-updating-applications.md)