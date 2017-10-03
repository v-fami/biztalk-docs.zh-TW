---
title: "（適用於 Azure) 的步驟 1： 建立 EDI 專案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d353129-04f0-456b-b371-b346959f5155
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb5f2e7af54ef99acff37a350c5fa7d9ba65af5e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-for-azure-create-the-edi-project"></a>（適用於 Azure) 的步驟 1： 建立 EDI 專案
在本節中，Contoso 會建立 EDI 專案使用[!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)]2012 年 4 月版。 專案的一部分，Contoso 新增下列各項：  
  
-   內部的銷售訂單結構描述 (**ECommerceSalesOrder.xsd**) 的 X12 840 EDI 銷售訂單結構描述都會被轉換。 Contoso 來處理訊息，接收到之後使用的內部結構描述[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
-   轉換 (**EDI840TOSALESORDER。TRFM**) 將 X12 840 銷售訂單結構描述以**ECommerceSalesOrder**結構描述。  
  
 Contoso 會使用這些成品在 Azure BizTalk 入口網站中建立協議時[!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)]。  
  
### <a name="to-create-edi-project"></a>若要建立 EDI 專案  
  
1.  開啟[!INCLUDE[vs2010](../includes/vs2010-md.md)]，從**檔案**功能表中的指向**新增**，然後按一下 **專案**。  
  
2.  在**新專案**對話方塊中，從**已安裝的範本**，選取**Service Bus**。 指定專案名稱和專案的位置，然後按一下**確定**。  
  
##  <a name="BKMK_CreateSchema"></a>若要建立 EDI 專案中的結構描述  
  
1.  從 方案總管 中，以滑鼠右鍵按一下您剛才建立的專案名稱，指向**新增**，然後按一下 **新項目**。  
  
2.  在**加入新項目**對話方塊中，從**已安裝的範本**，選取**結構描述**，指定做為結構描述名稱**ECommerceSalesOrder.xsd**，然後按一下 **新增**。  
  
3.  編輯和建置如下所示的結構描述：  
  
    ```  
    \<?xml version="1.0" encoding="utf-16"?>  
    \<xs:schema xmlns="http://ECommerceSalesOrder.Inbound" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" targetNamespace="http://ECommerceSalesOrder.Inbound" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
      \<xs:element name="SalesOrder">  
        \<xs:complexType>  
          \<xs:sequence>  
            \<xs:element name="CompanyCode" type="xs:string" />  
            \<xs:element name="PartID" type="xs:int" />  
            \<xs:element name="Quantity" type="xs:int" />  
            \<xs:element name="AskPrice" type="xs:decimal" />  
            \<xs:element name="RequestShipmentDate" type="xs:date" />  
            \<xs:element name="Address">  
              \<xs:complexType>  
                \<xs:sequence>  
                  \<xs:element name="Line1" type="xs:string" />  
                  \<xs:element name="Line2" type="xs:string" />  
                  \<xs:element name="City" type="xs:string" />  
                  \<xs:element name="State" type="xs:string" />  
                  \<xs:element name="Country" type="xs:string" />  
                  \<xs:element name="Zipcode" type="xs:int" />  
                \</xs:sequence>  
              \</xs:complexType>  
            \</xs:element>  
            \<xs:element name="Contact">  
              \<xs:complexType>  
                \<xs:sequence>  
                  \<xs:element name="Firstname" type="xs:string" />  
                  \<xs:element name="Lastname" type="xs:string" />  
                \</xs:sequence>  
              \</xs:complexType>  
            \</xs:element>  
            \<xs:element name="Comments" type="xs:string" />  
            \<xs:element name="DateNow" type="xs:date" />  
          \</xs:sequence>  
        \</xs:complexType>  
      \</xs:element>  
    \</xs:schema>  
    ```  
  
     您可以使用結構描述編輯器來建立此結構描述。 如需詳細資訊，請參閱[使用 BizTalk 編輯器](../core/using-biztalk-editor.md)。  
  
4.  儲存結構描述。  
  
##  <a name="BKMK_CreateTrfm"></a>若要建立 EDI 專案中的轉換  
  
1.  從 方案總管 中，以滑鼠右鍵按一下您剛才建立的專案名稱，指向**新增**，然後按一下 **新項目**。  
  
2.  在**加入新項目**對話方塊中，從**已安裝的範本**，選取**對應**，指定做為結構描述名稱**Edi840ToSalesOrder.trfm**，然後按一下 **新增**。  
  
3.  在對應中，針對來源結構描述選取**X12_00401_840.xsd**。 這是標準的 X12 EDI 銷售訂單結構描述。 您必須已經加入此結構描述您所建立的 EDI 專案。 您可以下載這個及其他 X12 結構描述從[http://go.microsoft.com/fwlink/p/?LinkId=235057](http://go.microsoft.com/fwlink/p/?LinkId=235057)。 X12 結構描述屬於**MicrosoftEdiXSDTemplates.zip**從下載位置可用的封裝。  
  
4.  針對目的地結構描述中，選取**ECommerceSalesOrder.xsd**。 您稍早在本主題中建立此結構描述。  
  
5.  連接的來源和目標結構描述中相關的節點，以建立對應。  
  
6.  儲存對應。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 4： 建立使用 BizTalk Server 2013 的混合式應用程式](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)