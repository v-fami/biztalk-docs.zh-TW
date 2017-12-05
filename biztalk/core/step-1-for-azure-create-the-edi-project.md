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
ms.openlocfilehash: 51264a79480031bd334dfb7d699a3a701f2c0254
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="step-1-for-azure-create-the-edi-project"></a><span data-ttu-id="d0b46-102">（適用於 Azure) 的步驟 1： 建立 EDI 專案</span><span class="sxs-lookup"><span data-stu-id="d0b46-102">Step 1 (For Azure): Create the EDI Project</span></span>
<span data-ttu-id="d0b46-103">在本節中，Contoso 會建立 EDI 專案使用[!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)]2012 年 4 月版。</span><span class="sxs-lookup"><span data-stu-id="d0b46-103">In this section, Contoso creates an EDI project using the [!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)] April 2012 release.</span></span> <span data-ttu-id="d0b46-104">專案的一部分，Contoso 新增下列各項：</span><span class="sxs-lookup"><span data-stu-id="d0b46-104">As part of the project, Contoso adds the following:</span></span>  
  
-   <span data-ttu-id="d0b46-105">內部的銷售訂單結構描述 (**ECommerceSalesOrder.xsd**) 的 X12 840 EDI 銷售訂單結構描述都會被轉換。</span><span class="sxs-lookup"><span data-stu-id="d0b46-105">An internal sales order schema (**ECommerceSalesOrder.xsd**) to which the X12 840 EDI sales order schema will be transformed.</span></span> <span data-ttu-id="d0b46-106">Contoso 來處理訊息，接收到之後使用的內部結構描述[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0b46-106">Contoso uses the internal schema to process the message after it is received into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="d0b46-107">轉換 (**EDI840TOSALESORDER。TRFM**) 將 X12 840 銷售訂單結構描述以**ECommerceSalesOrder**結構描述。</span><span class="sxs-lookup"><span data-stu-id="d0b46-107">A transform (**EDI840TOSALESORDER.TRFM**) to convert the X12 840 sales order schema to the **ECommerceSalesOrder** schema.</span></span>  
  
 <span data-ttu-id="d0b46-108">Contoso 會使用這些成品在 Azure BizTalk 入口網站中建立協議時[!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d0b46-108">Contoso uses these artifacts while creating an agreement in the Azure BizTalk portal in [!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)].</span></span>  
  
### <a name="to-create-edi-project"></a><span data-ttu-id="d0b46-109">若要建立 EDI 專案</span><span class="sxs-lookup"><span data-stu-id="d0b46-109">To create EDI project</span></span>  
  
1.  <span data-ttu-id="d0b46-110">開啟 Visual Studio 中，從**檔案**功能表中的指向**新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="d0b46-110">Open Visual Studio, from the **File** menu point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="d0b46-111">在**新專案**對話方塊中，從**已安裝的範本**，選取**Service Bus**。</span><span class="sxs-lookup"><span data-stu-id="d0b46-111">In the **New Project** dialog box, from the **Installed Templates**, select **Service Bus**.</span></span> <span data-ttu-id="d0b46-112">指定專案名稱和專案的位置，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d0b46-112">Specify a project name and a location for the project, and then click **OK**.</span></span>  
  
##  <a name="BKMK_CreateSchema"></a><span data-ttu-id="d0b46-113">若要建立 EDI 專案中的結構描述</span><span class="sxs-lookup"><span data-stu-id="d0b46-113">To create a schema within the EDI project</span></span>  
  
1.  <span data-ttu-id="d0b46-114">從 方案總管 中，以滑鼠右鍵按一下您剛才建立的專案名稱，指向**新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="d0b46-114">From the Solution Explorer, right-click the project name you just created, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="d0b46-115">在**加入新項目**對話方塊中，從**已安裝的範本**，選取**結構描述**，指定做為結構描述名稱**ECommerceSalesOrder.xsd**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="d0b46-115">In the **Add New Item** dialog box, from the **Installed Templates**, select **Schema**, specify the name of the schema as **ECommerceSalesOrder.xsd**, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="d0b46-116">編輯和建置如下所示的結構描述：</span><span class="sxs-lookup"><span data-stu-id="d0b46-116">Edit and build the schema to resemble the following:</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-16"?>  
    <xs:schema xmlns="http://ECommerceSalesOrder.Inbound" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" targetNamespace="http://ECommerceSalesOrder.Inbound" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
      <xs:element name="SalesOrder">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="CompanyCode" type="xs:string" />  
            <xs:element name="PartID" type="xs:int" />  
            <xs:element name="Quantity" type="xs:int" />  
            <xs:element name="AskPrice" type="xs:decimal" />  
            <xs:element name="RequestShipmentDate" type="xs:date" />  
            <xs:element name="Address">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="Line1" type="xs:string" />  
                  <xs:element name="Line2" type="xs:string" />  
                  <xs:element name="City" type="xs:string" />  
                  <xs:element name="State" type="xs:string" />  
                  <xs:element name="Country" type="xs:string" />  
                  <xs:element name="Zipcode" type="xs:int" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
            <xs:element name="Contact">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="Firstname" type="xs:string" />  
                  <xs:element name="Lastname" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
            <xs:element name="Comments" type="xs:string" />  
            <xs:element name="DateNow" type="xs:date" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:schema>  
    ```  
  
     <span data-ttu-id="d0b46-117">您可以使用結構描述編輯器來建立此結構描述。</span><span class="sxs-lookup"><span data-stu-id="d0b46-117">You can use the Schema Editor to build this schema.</span></span> <span data-ttu-id="d0b46-118">如需詳細資訊，請參閱[使用 BizTalk 編輯器](../core/using-biztalk-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="d0b46-118">For more information, see [Using BizTalk Editor](../core/using-biztalk-editor.md).</span></span>  
  
4.  <span data-ttu-id="d0b46-119">儲存結構描述。</span><span class="sxs-lookup"><span data-stu-id="d0b46-119">Save the schema.</span></span>  
  
##  <a name="BKMK_CreateTrfm"></a><span data-ttu-id="d0b46-120">若要建立 EDI 專案中的轉換</span><span class="sxs-lookup"><span data-stu-id="d0b46-120">To create a transform within the EDI project</span></span>  
  
1.  <span data-ttu-id="d0b46-121">從 方案總管 中，以滑鼠右鍵按一下您剛才建立的專案名稱，指向**新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="d0b46-121">From the Solution Explorer, right-click the project name you just created, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="d0b46-122">在**加入新項目**對話方塊中，從**已安裝的範本**，選取**對應**，指定做為結構描述名稱**Edi840ToSalesOrder.trfm**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="d0b46-122">In the **Add New Item** dialog box, from the **Installed Templates**, select **Map**, specify the name of the schema as **Edi840ToSalesOrder.trfm**, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="d0b46-123">在對應中，針對來源結構描述選取**X12_00401_840.xsd**。</span><span class="sxs-lookup"><span data-stu-id="d0b46-123">In the map, for the source schema select **X12_00401_840.xsd**.</span></span> <span data-ttu-id="d0b46-124">這是標準的 X12 EDI 銷售訂單結構描述。</span><span class="sxs-lookup"><span data-stu-id="d0b46-124">This is the standard X12 schema for an EDI sales order.</span></span> <span data-ttu-id="d0b46-125">您必須已經加入此結構描述您所建立的 EDI 專案。</span><span class="sxs-lookup"><span data-stu-id="d0b46-125">You must have already added this schema to the EDI project you created.</span></span> <span data-ttu-id="d0b46-126">您可以下載這個及其他 X12 結構描述從[http://go.microsoft.com/fwlink/p/?LinkId=235057](http://go.microsoft.com/fwlink/p/?LinkId=235057)。</span><span class="sxs-lookup"><span data-stu-id="d0b46-126">You can download this, and other X12 schemas from [http://go.microsoft.com/fwlink/p/?LinkId=235057](http://go.microsoft.com/fwlink/p/?LinkId=235057).</span></span> <span data-ttu-id="d0b46-127">X12 結構描述屬於**MicrosoftEdiXSDTemplates.zip**從下載位置可用的封裝。</span><span class="sxs-lookup"><span data-stu-id="d0b46-127">The X12 schemas are part of the **MicrosoftEdiXSDTemplates.zip** package available from the download location.</span></span>  
  
4.  <span data-ttu-id="d0b46-128">針對目的地結構描述中，選取**ECommerceSalesOrder.xsd**。</span><span class="sxs-lookup"><span data-stu-id="d0b46-128">For the destination schema, select **ECommerceSalesOrder.xsd**.</span></span> <span data-ttu-id="d0b46-129">您稍早在本主題中建立此結構描述。</span><span class="sxs-lookup"><span data-stu-id="d0b46-129">You created this schema earlier in this topic.</span></span>  
  
5.  <span data-ttu-id="d0b46-130">連接的來源和目標結構描述中相關的節點，以建立對應。</span><span class="sxs-lookup"><span data-stu-id="d0b46-130">Create the map by connecting the relevant nodes in the source and target schemas.</span></span>  
  
6.  <span data-ttu-id="d0b46-131">儲存對應。</span><span class="sxs-lookup"><span data-stu-id="d0b46-131">Save the map.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0b46-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="d0b46-132">See Also</span></span>  
 [<span data-ttu-id="d0b46-133">教學課程 4： 建立使用 BizTalk Server 2013 的混合式應用程式</span><span class="sxs-lookup"><span data-stu-id="d0b46-133">Tutorial 4: Creating a Hybrid Application Using BizTalk Server 2013</span></span>](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)