---
title: "結構描述中的類別目錄新增配接器中繼資料精靈 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3927c676-f60a-449e-be43-6f75e28aefe1
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4fda24ee5ef4993c90eb82e0f406da2e06618776
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="schema-categories-in-the-add-adapter-metadata-wizard"></a>新增配接器中繼資料精靈中的結構描述類別

## <a name="overview"></a>概觀
> [!NOTE]
>  本主題是僅針對靜態配接器可實作**IStaticAdapterConfig**介面。  
  
 在將資料傳遞到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 之前，配接器可能會使用數千種結構描述中的一種來進行轉換。 在將中繼資料新增到 BizTalk 專案時，請使用 [新增配接器中繼資料精靈]，從配接器與其互動之所有結構描述的清單中，選取某個結構描述。  
  
 在範例檔案配接器中，CategorySchema.xml 檔案是與配接器架構的 BiztalkAdapterFramework.xsd 檔案搭配使用，以填入服務結構描述之樹狀檢視組織的結構描述執行個體。  BizTalkAdapterFramework.xsd 檔案位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Developer Tools 資料夾中。  
  
 您應該建立這個檔案，以便以能夠從您解決方案直接取得的方式來組織結構描述。 CategorySchema.xml 中的現有類別只是您可以在自己的樹狀結構中做到的範例。 這些類別與範例配接器所傳遞的資料沒有任何特別關係。 結構描述的組織對於應用程式的特定配接器尤其重要，因為其中可能會有數千種不同的結構描述。 對於傳輸的特定配接器，這個樹狀檢視組織是不必要的。  
  
 下圖顯示**選取要匯入服務**中新增配接器中繼資料精靈頁面。  
  
 ![](../core/media/ebiz-prog-custad-tree.gif "ebiz_prog_custad_tree")  
[新增配接器中繼資料精靈] 中結構描述類別的樹狀檢視  


## <a name="sample-xml"></a>範例 XML
  
 下列程式碼顯示 CategorySchema.xml 檔案：  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<CategoryTree>  
     <DisplayName>Services Organization</DisplayName>  
     <DisplayDescription>An organization of application services</DisplayDescription>  
     <CategoryTreeNode>  
          <DisplayName>Health Care</DisplayName>  
          <Description>Services under Health Care</Description>  
          <CategoryTreeNode>  
               <DisplayName>Administrative</DisplayName>  
               <Description>Administrative Health Care Services</Description>  
               <ServiceTreeNode>  
                    <DisplayName>Eligibility</DisplayName>  
                    <Description>Eligibility Verification Transactions</Description>  
                    <WSDLReference>ANSI X 12 270</WSDLReference>  
               </ServiceTreeNode>  
          </CategoryTreeNode>  
     </CategoryTreeNode>  
     <CategoryTreeNode>  
          <DisplayName>Manufacturing</DisplayName>  
          <Description>Manufacturing Services</Description>  
          <CategoryTreeNode>  
               <DisplayName>Inventory</DisplayName>  
               <Description>Inventory Services</Description>  
               <ServiceTreeNode>  
                    <DisplayName>Requisition</DisplayName>  
                    <Description>Requisition</Description>  
                    <WSDLReference>RequisitionService</WSDLReference>  
               </ServiceTreeNode>  
          </CategoryTreeNode>  
     </CategoryTreeNode>  
</CategoryTree>  
```  
  
 下列節點類型出現在此結構描述執行個體中：  
  
-   **CategoryTree。** 系統資訊之模型的最上層結構。 包含零個或多個 CategoryTreeNode、ExpandableCategoryTreeNode 及 ServiceTreeNode 節點。  
  
-   **CategoryTreeNode。** 包含零個或多個 CategoryTreeNode 和 ServiceTreeNode 節點。 使用在使用者介面 (UI) 中出現為資料夾的 CategoryTreeNode，將相關的一組服務編成群組。 通常這會包含顯示名稱和所要顯示之服務的描述。 如果子節點的數目不大，配接器便可以使用 CategoryTreeNode。  
  
-   **ExpandableCategoryTreeNode。** 在展開時便會被動態地填入的分葉節點。 ExpandableCategoryTreeNode 具有預留位置的用途，並會在 UI 中以資料夾的形式出現。 在使用者按一下以展開節點前，這可以用來延遲以子項目填入類別節點。 如果類別包含大量子節點，配接器便可以使用 ExpandableCategoryTreeNode。  
  
-   **ServiceTreeNode。** ServiceTreeNode 會出現為文件，或是 UI 中的分葉節點，並代表 Web 服務描述語言 (WSDL) 檔案。  
  
 當使用者按一下資料夾以展開節點時，配接器架構會呼叫**IStaticAdapterConfig.GetServiceOrganization**方法傳遞做為值的節點名稱的介面卡上**Istaticadapterconfig.getserviceorganization**屬性。 配接器應該會傳回一個 CategoryTree，其中包含要在 ExpandableCategoryTreeNode 下新增的子節點。 配接器架構會將 ExpandableCategoryTreeNode 取代為 CategoryTreeNode，並將其新增到傳回之 CategoryTree 的子系。  
  
> [!NOTE]
>  在初始呼叫**IStaticAdapterConfig.GetServiceOrganization**配接器架構傳遞 null 給節點識別碼。 這樣便會告知配接器傳回根層級的 CategoryTree。  
  
 以下是從 BiztalkAdapterFramework.xsd 檔案中擷取的類別樹狀結構描述。 這會由 [新增配接器中繼資料精靈] 用來做為骨幹樹狀結構，並在其中填入 XML 檔案中的特定應用程式相依實體。 在我們的範例中，該檔案是 CategorySchema.xml 檔案。  
  
```  
<!-- Service Organization Tree schema used by Add Adapter Wizard -->  
    <xs:element name="CategoryTree" type="CategoryTree" />  
    <xs:complexType name="CategoryTree">  
        <xs:sequence>  
            <xs:element name="DisplayName" type="xs:string" />  
            <xs:element name="DisplayDescription" type="xs:string" />  
            <xs:choice minOccurs="0" maxOccurs="unbounded">  
                <xs:element name="ExpandableCategoryTreeNode" type="ExpandableCategoryTreeNode" minOccurs="0" maxOccurs="unbounded" />  
                <xs:element name="CategoryTreeNode" type="CategoryTreeNode" minOccurs="0" maxOccurs="unbounded" />  
                <xs:element name="ServiceTreeNode" type="ServiceTreeNode" minOccurs="0" maxOccurs="unbounded" />  
            </xs:choice>  
        </xs:sequence>  
    </xs:complexType>  
    <xs:complexType name="ExpandableCategoryTreeNode">  
        <xs:sequence>  
            <xs:element name="DisplayName" type="xs:string" />  
            <xs:element name="Description" type="xs:string" />  
        </xs:sequence>  
        <xs:attribute name="NodeIdentifier" type="xs:string" use="required"></xs:attribute>  
    </xs:complexType>  
    <xs:complexType name="CategoryTreeNode">  
        <xs:sequence>  
            <xs:element name="DisplayName" type="xs:string" />  
            <xs:element name="Description" type="xs:string" />  
            <xs:choice minOccurs="0" maxOccurs="unbounded">  
                <xs:element name="ExpandableCategoryTreeNode" type="ExpandableCategoryTreeNode" minOccurs="0" maxOccurs="unbounded" />  
                <xs:element name="CategoryTreeNode" type="CategoryTreeNode" minOccurs="0" maxOccurs="unbounded" />  
                <xs:element name="ServiceTreeNode" type="ServiceTreeNode" minOccurs="0" maxOccurs="unbounded" />  
            </xs:choice>  
        </xs:sequence>  
    </xs:complexType>  
    <xs:complexType name="ServiceTreeNode">  
        <xs:sequence>  
            <xs:element name="DisplayName" type="xs:string" />  
            <xs:element name="Description" type="xs:string" />  
            <xs:element name="WSDLReference" type="xs:string" />  
        </xs:sequence>  
    </xs:complexType>  
</xs:schema>  
```  
  
 在修改過您的 CategorySchema.xml 檔案後，重新建置 AdapterManagement 專案，然後執行 [新增配接器中繼資料精靈]，確定 CategorySchema.xml 中表示的樹狀結構有正確出現。  
  
 執行 「 新增配接器中繼資料精靈 」 的相關資訊，請參閱**新增配接器中繼資料精靈 對話方塊** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。