---
title: 步驟 6 （內部部署）： 建立轉換以從佇列將訊息插入結構描述對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30a55f1e-32cc-409a-a814-084026f51b35
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ae0bc6826bda147d4af6ccb47d81eb2513eea640
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981303"
---
# <a name="step-6-on-premises-create-a-transform-to-map-the-message-from-the-queue-to-the-insert-schema"></a>步驟 6 （內部部署）： 建立轉換以從佇列將訊息插入結構描述對應
收到的訊息[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]來自服務匯流排佇列將屬於**ECommerceSalesOrder.xsd**結構描述。 不過，若要將訊息插入**SalesOrder**資料表中，訊息必須屬於**插入**中產生的結構描述[步驟 5 （內部部署）： 產生將訊息插入至結構描述SalesOrder 資料表](../core/step-5-generate-the-schema-for-inserting-a-message-into-salesorder-table.md)。 因此，如本主題中，我們可以建立對應來轉換**ECommerceSalesOrder.xsd**成插入作業結構描述的結構描述。  

### <a name="to-create-a-map"></a>若要建立對應  

1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]您已經建立，以滑鼠右鍵按一下專案，指向**新增**，然後按一下**新項目**。 在**新的項目**對話方塊中，選取**對應**，輸入對應名稱為`SalesOrder_SQL.btm`，然後按一下**新增**。  

2. 在對應中，針對來源結構描述中，選取**ECommerceSalesOrder.xsd**。 針對目的地結構描述中，選取**TableOperations.SalesOrder.xsd (Insert)** 結構描述。  

3. 直接對應來源與目的結構描述中的下列節點：  


   | 來源結構描述 | 目的結構描述 |
   |---------------|--------------------|
   |  CompanyCode  |    CompanyCode     |
   |    PartId     |      PartNum       |
   |   Quantity    |        Qty         |
   |   AskPrice    |    UnitAskPrice    |
   |   註解    |  CustomerComments  |


4. 使用**日期和時間**」 運算質，將值對應至**DateRequested**並**ShipDate**目的結構描述中的項目。 這些節點未對應至來源結構描述中的個別節點。 相反地，目前的日期和時間會傳遞給這些節點使用**日期和時間**運算質。  

   1.  將拖放**日期和時間**」 運算質從工具箱 拖曳至對應工具介面。  

   2.  連接到運算質**DateRequested**目的結構描述中的項目。  

   3.  拖放另一個**日期和時間**運算質並將其連接到**ShipDate**目的結構描述中的項目。  

5. 對應中使用的來源和目的地結構描述的下列節點**字串串連**運算質：  

   |來源結構描述|目的結構描述|  
   |-------------------|------------------------|  
   |Address\Line1|SellToAddress<br /><br /> BillToAddress|  
   |Address\Line2|SellToAddress<br /><br /> BillToAddress|  
   |Address\City|SellToAddress<br /><br /> BillToAddress|  
   |Address\State|SellToAddress<br /><br /> BillToAddress|  
   |Address\Country|SellToAddress<br /><br /> BillToAddress|  
   |Address\ZipCode|SellToAddress<br /><br /> BillToAddress|  
   |Contact\FirstName|PartnerContact|  
   |Contact\LastName||  

    針對各字串串連對應集執行下列步驟：  

   1.  將拖放**字串串連**」 運算質從工具箱 拖曳至對應工具介面。  

   2.  從來源樹狀結構的每個項目新增至做為輸入**字串串連**運算質。  

   3.  拖曳並設定的輸出**字串串連**」 運算質至目的結構描述中的項目。  

        完整的對應看起來如下：  

        ![要轉換結構描述對應](../core/media/bts2010r2-tut1-map.jpg "BTS2010R2_Tut1_Map")  

## <a name="see-also"></a>另請參閱  
 [教學課程 4： 建立使用 BizTalk Server 2013 的混合式應用程式](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)