---
title: 步驟 3b： 使用 Wcf-webhttp 配接器從 Salesforce 擷取機會詳細資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 115c908f-777b-4c51-85ea-71d639b01775
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66337277e2a84edbe8802b739988bcee030bc054
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008111"
---
# <a name="step-3b-retrieve-opportunity-details-from-salesforce-using-the-wcf-webhttp-adapter"></a><span data-ttu-id="c70f4-102">步驟 3b： 使用 Wcf-webhttp 配接器從 Salesforce 擷取機會詳細資料</span><span class="sxs-lookup"><span data-stu-id="c70f4-102">Step 3b: Retrieve Opportunity Details from Salesforce using the WCF-WebHttp Adapter</span></span>
<span data-ttu-id="c70f4-103">在本節中，我們會著重於處理內送商機通知的協調流程、從通知擷取商機名稱，並用來建立要求查詢以傳送至 Salesforce。</span><span class="sxs-lookup"><span data-stu-id="c70f4-103">In this section, we’ll enhance the orchestration to process the incoming opportunity notification, extract the opportunity name from the notification, and use that to create a request query to send to Salesforce.</span></span> <span data-ttu-id="c70f4-104">這樣會擷取與商機關聯的產品相關特定詳細資料。</span><span class="sxs-lookup"><span data-stu-id="c70f4-104">This retrieves specific details about the products associated with the opportunity.</span></span> <span data-ttu-id="c70f4-105">來自 Salesforce 的查詢回應會由 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收。</span><span class="sxs-lookup"><span data-stu-id="c70f4-105">The query response from Salesforce is received back into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="c70f4-106">若要達到此目標，我們會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="c70f4-106">To achieve this, we’ll perform the following steps:</span></span>  
  
-   <span data-ttu-id="c70f4-107">建立結構描述和訊息變數以傳送查詢訊息至 Salesforce。</span><span class="sxs-lookup"><span data-stu-id="c70f4-107">Create a schema and message variables to send a query message to Salesforce.</span></span>  
  
-   <span data-ttu-id="c70f4-108">建立對應以使用商機通知中的值來建立查詢以擷取與該商機相關聯的產品詳細資料。</span><span class="sxs-lookup"><span data-stu-id="c70f4-108">Create a map to use the values from the opportunity notification for creating a query to retrieve product details associated with the opportunity.</span></span>  
  
-   <span data-ttu-id="c70f4-109">建立結構描述以接收來自 Salesforce 的查詢回應。</span><span class="sxs-lookup"><span data-stu-id="c70f4-109">Create a schema to receive a query response from Salesforce.</span></span>  
  
-   <span data-ttu-id="c70f4-110">為要求和回應結構描述建立訊息變數。</span><span class="sxs-lookup"><span data-stu-id="c70f4-110">Create message variables for the request and response schemas.</span></span>  
  
## <a name="create-schema-and-message-variables-to-send-query-messages-to-salesforce"></a><span data-ttu-id="c70f4-111">建立結構描述和訊息變數，以傳送查詢訊息至 Salesforce</span><span class="sxs-lookup"><span data-stu-id="c70f4-111">Create Schema and Message Variables to Send Query Messages to Salesforce</span></span>  
 <span data-ttu-id="c70f4-112">若要使用可透過商機通知的資訊從 Salesforce 擷取產品詳細資料，我們需要將查詢傳送到 Salesforce。</span><span class="sxs-lookup"><span data-stu-id="c70f4-112">To retrieve product details from Salesforce by using the information available through an Opportunity notification, we need to send a query to Salesforce.</span></span> <span data-ttu-id="c70f4-113">做為 XML 訊息會將查詢傳送到 Salesforce。</span><span class="sxs-lookup"><span data-stu-id="c70f4-113">The query is sent to Salesforce as an XML message.</span></span> <span data-ttu-id="c70f4-114">因此，下列程序建立要求訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="c70f4-114">So, in the following procedure we create a schema for the request message.</span></span> <span data-ttu-id="c70f4-115">在後續的程序中，我們將對應的商機通知的結構描述與此結構描述，來建構查詢，以擷取產品詳細資料的機會。</span><span class="sxs-lookup"><span data-stu-id="c70f4-115">In the subsequent procedure, we will map the opportunity notification schema with this schema to construct a query for retrieving product details for the opportunity.</span></span>  
  
#### <a name="to-create-a-schema-for-sending-query-request"></a><span data-ttu-id="c70f4-116">若要建立傳送查詢要求的結構描述</span><span class="sxs-lookup"><span data-stu-id="c70f4-116">To create a schema for sending query request</span></span>  
  
1. <span data-ttu-id="c70f4-117">加入新的結構描述[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案。</span><span class="sxs-lookup"><span data-stu-id="c70f4-117">Add a new schema to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.</span></span> <span data-ttu-id="c70f4-118">將它命名為 `QueryRequest.xsd`。</span><span class="sxs-lookup"><span data-stu-id="c70f4-118">Name it `QueryRequest.xsd`.</span></span>  
  
2. <span data-ttu-id="c70f4-119">重新命名的根節點`QueryRequest`。</span><span class="sxs-lookup"><span data-stu-id="c70f4-119">Rename the root node to `QueryRequest`.</span></span> <span data-ttu-id="c70f4-120">新增 QueryRequest 記錄下的子欄位項目並將它命名`Query`。</span><span class="sxs-lookup"><span data-stu-id="c70f4-120">Add a child field element under the QueryRequest record and name it `Query`.</span></span>  
  
3. <span data-ttu-id="c70f4-121">升階**查詢**結構描述，使其可供協調流程內的使用中的項目。</span><span class="sxs-lookup"><span data-stu-id="c70f4-121">Promote the **Query** element in the schema so that it is available for use within the orchestration.</span></span> <span data-ttu-id="c70f4-122">在接下來的步驟中，我們將使用此升級的項目來將查詢字串指定。</span><span class="sxs-lookup"><span data-stu-id="c70f4-122">In the later steps we will use this promoted element to assign the query string.</span></span>  
  
    <span data-ttu-id="c70f4-123">以滑鼠右鍵按一下**查詢**項目，指向**升階**，然後按一下**快速升級**。</span><span class="sxs-lookup"><span data-stu-id="c70f4-123">Right-click the **Query** element, point to **Promote**, and then click **Quick Promotions**.</span></span> <span data-ttu-id="c70f4-124">這會導致建立**PropertySchema.xsd**結構描述**查詢**項目。</span><span class="sxs-lookup"><span data-stu-id="c70f4-124">This results in creating a **PropertySchema.xsd** schema with a **Query** element.</span></span> <span data-ttu-id="c70f4-125">請注意命名空間，如 PropertySchema。</span><span class="sxs-lookup"><span data-stu-id="c70f4-125">Note the namespace for the PropertySchema.</span></span> <span data-ttu-id="c70f4-126">您必須在未來此步驟在設定中的實體連接埠[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="c70f4-126">You will need this in the future steps while configuring the physical ports in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
4. <span data-ttu-id="c70f4-127">儲存所有變更。</span><span class="sxs-lookup"><span data-stu-id="c70f4-127">Save all changes.</span></span>  
  
## <a name="map-the-opportunity-notification-schema-to-the-query-schema"></a><span data-ttu-id="c70f4-128">商機通知結構描述對應至查詢的結構描述</span><span class="sxs-lookup"><span data-stu-id="c70f4-128">Map the Opportunity Notification Schema to the Query Schema</span></span>  
 <span data-ttu-id="c70f4-129">若要擷取與商機相關聯的產品詳細資料，我們需要類似下列的查詢傳送到 Salesforce:</span><span class="sxs-lookup"><span data-stu-id="c70f4-129">To retrieve the product details associated with the opportunity, we need to send a query similar to the following to Salesforce:</span></span>  
  
```  
SELECT Amount, Id, Name,(SELECT Quantity, ListPrice, PricebookEntry.UnitPrice, PricebookEntry.Name FROM OpportunityLineItems) FROM Opportunity Where Name = '<opportunity_name>'  
```  
  
 <span data-ttu-id="c70f4-130">在上一個程序中我們已經建立查詢訊息結構的描述。</span><span class="sxs-lookup"><span data-stu-id="c70f4-130">In the previous procedure we already created the schema of the query message.</span></span> <span data-ttu-id="c70f4-131">在此程序中，我們有機會通知結構描述對應至查詢要求結構描述，並使用運算質來建構這個查詢。</span><span class="sxs-lookup"><span data-stu-id="c70f4-131">In this procedure, we map the opportunity notification schema to the query request schema and use functoids to construct this query.</span></span> <span data-ttu-id="c70f4-132">此查詢，會當做值傳遞給**查詢**中的項目**QueryRequest.xsd**結構描述。</span><span class="sxs-lookup"><span data-stu-id="c70f4-132">This query will be passed as a value to the **Query** element in the **QueryRequest.xsd** schema.</span></span>  
  
#### <a name="to-map-the-opportunity-notification"></a><span data-ttu-id="c70f4-133">若要將商機通知的對應</span><span class="sxs-lookup"><span data-stu-id="c70f4-133">To map the opportunity notification</span></span>  
  
1. <span data-ttu-id="c70f4-134">將地圖加入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案。</span><span class="sxs-lookup"><span data-stu-id="c70f4-134">Add a map to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.</span></span> <span data-ttu-id="c70f4-135">命名對應`Notification_QueryRequest.btm`。</span><span class="sxs-lookup"><span data-stu-id="c70f4-135">Name the map `Notification_QueryRequest.btm`.</span></span>  
  
2. <span data-ttu-id="c70f4-136">若要設定來源結構描述**NotificationService_soap_sforce_com_2005_09_outbound.xsd**。</span><span class="sxs-lookup"><span data-stu-id="c70f4-136">Set the source schema to **NotificationService_soap_sforce_com_2005_09_outbound.xsd**.</span></span> <span data-ttu-id="c70f4-137">設定為目的結構描述**QueryRequest**.xsd。</span><span class="sxs-lookup"><span data-stu-id="c70f4-137">Set the destination schema to **QueryRequest**.xsd.</span></span>  
  
3. <span data-ttu-id="c70f4-138">新增**字串串連**」 運算質至對應的介面。</span><span class="sxs-lookup"><span data-stu-id="c70f4-138">Add a **String Concatenate** functoid to the mapping surface.</span></span> <span data-ttu-id="c70f4-139">開啟**設定字串串連運算質**對話方塊方塊，並指定輸入的值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c70f4-139">Open the **Configure String Concatenate Functoid** dialog box and specify the input values as follows:</span></span>  
  
   |||  
   |-|-|  
   |<span data-ttu-id="c70f4-140">輸入 [0]</span><span class="sxs-lookup"><span data-stu-id="c70f4-140">Input[0]</span></span>|<span data-ttu-id="c70f4-141">選取數量、 識別碼、 名稱 (選取 Quantity、 ListPrice PricebookEntry.UnitPrice，PricebookEntry.Name 從 OpportunityLineItems) 有機會從 Where Name = '</span><span class="sxs-lookup"><span data-stu-id="c70f4-141">SELECT Amount, Id, Name,(SELECT Quantity, ListPrice, PricebookEntry.UnitPrice, PricebookEntry.Name FROM OpportunityLineItems) FROM Opportunity Where Name = '</span></span>|  
   |<span data-ttu-id="c70f4-142">輸入 [1]</span><span class="sxs-lookup"><span data-stu-id="c70f4-142">Input[1]</span></span>|<span data-ttu-id="c70f4-143">連接來源結構描述中的名稱項目 」 運算質使用 Name 元素的值做為第二個輸入。</span><span class="sxs-lookup"><span data-stu-id="c70f4-143">Connect the Name element in the source schema to the functoid to use the value of the Name element as the second input.</span></span>|  
   |<span data-ttu-id="c70f4-144">輸入 [2]</span><span class="sxs-lookup"><span data-stu-id="c70f4-144">Input[2]</span></span>|<span data-ttu-id="c70f4-145">'**附註：** 最後一個的輸入值，指定只有右單一引號 （'）。</span><span class="sxs-lookup"><span data-stu-id="c70f4-145">' **Note:**  For the last input value, specify only a closing single quote (').</span></span>|  
  
    <span data-ttu-id="c70f4-146">下列螢幕擷取畫面描述的組態**字串串連**運算質。</span><span class="sxs-lookup"><span data-stu-id="c70f4-146">The following screenshot depicts the configuration for the **String Concatenate** functoid.</span></span>  
  
    <span data-ttu-id="c70f4-147">![設定字串串連運算質](../core/media/bts-sf-stringconcatenate.jpg "BTS_SF_StringConcatenate")</span><span class="sxs-lookup"><span data-stu-id="c70f4-147">![Configure String Concatenate functoid](../core/media/bts-sf-stringconcatenate.jpg "BTS_SF_StringConcatenate")</span></span>  
  
    <span data-ttu-id="c70f4-148">當串連三個輸入的參數時，它將會形成所需的查詢傳送到 Salesforce。</span><span class="sxs-lookup"><span data-stu-id="c70f4-148">When the three input parameters are concatenated, it will form the required query to be sent to Salesforce.</span></span>  
  
4. <span data-ttu-id="c70f4-149">連接字串串連運算質至目的結構描述中的查詢項目，如下列螢幕擷取畫面所示。</span><span class="sxs-lookup"><span data-stu-id="c70f4-149">Connect the String Concatenate functoid to the Query element in the destination schema, as shown in the following screenshot.</span></span>  
  
    <span data-ttu-id="c70f4-150">![對應至查詢的結構描述的通知回應](../core/media/bts-sf-notification-query-mapping.jpg "BTS_SF_Notification_Query_Mapping")</span><span class="sxs-lookup"><span data-stu-id="c70f4-150">![Map notification response to query schema](../core/media/bts-sf-notification-query-mapping.jpg "BTS_SF_Notification_Query_Mapping")</span></span>  
  
5. <span data-ttu-id="c70f4-151">儲存對應變更。</span><span class="sxs-lookup"><span data-stu-id="c70f4-151">Save changes to the map.</span></span>  
  
## <a name="creating-schema-to-receive-the-query-response-message"></a><span data-ttu-id="c70f4-152">建立接收查詢回應訊息的結構描述</span><span class="sxs-lookup"><span data-stu-id="c70f4-152">Creating Schema to Receive the Query Response Message</span></span>  
 <span data-ttu-id="c70f4-153">在本節中，我們會建立要接收來自 Salesforce 的查詢回應訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="c70f4-153">In this section, we create the schema to receive the query response message from Salesforce.</span></span> <span data-ttu-id="c70f4-154">在本節中，我們可以手動建立查詢回應結構的描述。</span><span class="sxs-lookup"><span data-stu-id="c70f4-154">In this section, we manually create the schema for the query response.</span></span>  
  
#### <a name="to-create-a-schema-to-receive-the-query-response"></a><span data-ttu-id="c70f4-155">若要建立接收查詢回應結構描述</span><span class="sxs-lookup"><span data-stu-id="c70f4-155">To create a schema to receive the query response</span></span>  
  
1. <span data-ttu-id="c70f4-156">加入新的結構描述[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案，並命名`QueryResult.xsd`。</span><span class="sxs-lookup"><span data-stu-id="c70f4-156">Add a new schema to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project and name it `QueryResult.xsd`.</span></span>  
  
2. <span data-ttu-id="c70f4-157">Salesforce [QueryResult](http://go.microsoft.com/fwlink/?LinkId=287017)物件描述從 Salesforce 收到的查詢回應。</span><span class="sxs-lookup"><span data-stu-id="c70f4-157">The Salesforce [QueryResult](http://go.microsoft.com/fwlink/?LinkId=287017) object depicts the query response received from Salesforce.</span></span> <span data-ttu-id="c70f4-158">因此，我們將建置結構描述來描述下列：</span><span class="sxs-lookup"><span data-stu-id="c70f4-158">So, we’ll build a schema to depict the following:</span></span>  
  
   ```  
   <?xml version="1.0" encoding="utf-16" ?>  
   - <xs:schema xmlns="http://BtsSalesforceIntegration.QueryResult" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" targetNamespace="http://BtsSalesforceIntegration.QueryResult" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
     - <xs:element name="QueryResult">  
       - <xs:complexType>  
         - <xs:sequence>  
           <xs:element name="done" type="xs:string" />  
           - <xs:sequence>  
             - <xs:element name="records">  
               - <xs:complexType>  
                 - <xs:sequence>  
                   <xs:element name="Id" type="xs:string" />  
                   <xs:element name="Amount" type="xs:string" />  
                   <xs:element name="Name" type="xs:string" />  
                   - <xs:sequence>  
                     - <xs:element name="OpportunityLineItems">  
                       - <xs:complexType>  
                         - <xs:sequence>  
                           <xs:element name="done" type="xs:string" />  
                           - <xs:sequence minOccurs="1" maxOccurs="unbounded">  
                             - <xs:element name="records">  
                               - <xs:complexType>  
                                 - <xs:sequence>  
                                   <xs:element name="Quantity" type="xs:string" />  
                                   <xs:element name="ListPrice" type="xs:string" />  
                                   - <xs:element name="PricebookEntry">  
                                     - <xs:complexType>  
                                       - <xs:sequence>  
                                         <xs:element name="UnitPrice" type="xs:string" />  
                                         <xs:element name="Name" type="xs:string" />  
                                       </xs:sequence>  
                                       <xs:attribute name="type" type="xs:string" />  
                                       <xs:attribute name="url" type="xs:string" />  
                                     </xs:complexType>  
                                   </xs:element>  
                                 </xs:sequence>  
                                 <xs:attribute name="type" type="xs:string" />  
                                 <xs:attribute name="url" type="xs:string" />  
                               </xs:complexType>  
                             </xs:element>  
                           </xs:sequence>  
                           <xs:element name="totalSize" type="xs:string" />  
                         </xs:sequence>  
                       </xs:complexType>  
                     </xs:element>  
                   </xs:sequence>  
                 </xs:sequence>  
                 <xs:attribute name="type" type="xs:string" />  
                 <xs:attribute name="url" type="xs:string" />  
               </xs:complexType>  
             </xs:element>  
           </xs:sequence>  
           <xs:element name="totalSize" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
     </xs:element>  
   </xs:schema>  
   ```  
  
    <span data-ttu-id="c70f4-159">結構描述結構看起來應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="c70f4-159">The schema structure should look like the following:</span></span>  
  
    <span data-ttu-id="c70f4-160">![來自 Salesforce 的查詢回應的結構描述](../core/media/bts-sf-queryresult.jpg "BTS_SF_QueryResult")</span><span class="sxs-lookup"><span data-stu-id="c70f4-160">![Schema for query response from Salesforce](../core/media/bts-sf-queryresult.jpg "BTS_SF_QueryResult")</span></span>  
  
3. <span data-ttu-id="c70f4-161">儲存結構描述變更。</span><span class="sxs-lookup"><span data-stu-id="c70f4-161">Save changes to the schema.</span></span>  
  
## <a name="create-message-variables-for-queryrequest-and-queryresult-schemas"></a><span data-ttu-id="c70f4-162">建立訊息變數 QueryRequest 和 QueryResult 結構描述</span><span class="sxs-lookup"><span data-stu-id="c70f4-162">Create Message Variables for QueryRequest and QueryResult Schemas</span></span>  
 <span data-ttu-id="c70f4-163">您已建立之 QueryRequest 和 QueryResult 結構描述之後，您必須建立兩個訊息變數來代表兩個訊息類型的協調流程中。</span><span class="sxs-lookup"><span data-stu-id="c70f4-163">After you have created the QueryRequest and QueryResult schemas, you must create two message variables in the orchestration to represent the two message types.</span></span>  
  
#### <a name="to-create-message-variables"></a><span data-ttu-id="c70f4-164">建立訊息變數</span><span class="sxs-lookup"><span data-stu-id="c70f4-164">To create message variables</span></span>  
  
1.  <span data-ttu-id="c70f4-165">開啟**NotificationService.odx**協調流程，並在協調流程檢視中，新增兩個新的訊息。</span><span class="sxs-lookup"><span data-stu-id="c70f4-165">Open the **NotificationService.odx** orchestration and in the orchestration view, add two new messages.</span></span> <span data-ttu-id="c70f4-166">設定訊息名稱，作為`QueryRequestMsg`和`QueryResultMsg`。</span><span class="sxs-lookup"><span data-stu-id="c70f4-166">Set the message names as `QueryRequestMsg` and `QueryResultMsg`.</span></span>  
  
2.  <span data-ttu-id="c70f4-167">設定的訊息類型**QueryRequestMsg**作為**BtsSalesforceIntegration.QueryRequest**。</span><span class="sxs-lookup"><span data-stu-id="c70f4-167">Set the message type for **QueryRequestMsg** as **BtsSalesforceIntegration.QueryRequest**.</span></span>  
  
3.  <span data-ttu-id="c70f4-168">設定的訊息類型**QueryResultMsg**作為**BtsSalesforceIntegration.QueryResult**。</span><span class="sxs-lookup"><span data-stu-id="c70f4-168">Set the message type for **QueryResultMsg** as **BtsSalesforceIntegration.QueryResult**.</span></span>  
  
4.  <span data-ttu-id="c70f4-169">將變更儲存至協調流程。</span><span class="sxs-lookup"><span data-stu-id="c70f4-169">Save changes to the orchestration.</span></span>  
  
## <a name="update-the-orchestration-to-send-message-to-salesforce-and-receive-a-response"></a><span data-ttu-id="c70f4-170">更新協調流程將訊息傳送到 Salesforce 並接收回應</span><span class="sxs-lookup"><span data-stu-id="c70f4-170">Update the Orchestration to Send Message to Salesforce and Receive a Response</span></span>  
 <span data-ttu-id="c70f4-171">主題中[步驟 3a： 到 BizTalk Server 接收 Salesforce Opportunity Notification](../core/step-3a-receive-salesforce-opportunity-notification-into-biztalk-server.md)，我們建立的協調流程會接收來自 Salesforce 商機通知並傳送通知。</span><span class="sxs-lookup"><span data-stu-id="c70f4-171">In the topic [Step 3a: Receive Salesforce Opportunity Notification into BizTalk Server](../core/step-3a-receive-salesforce-opportunity-notification-into-biztalk-server.md), we built the orchestration that receives opportunity notifications from Salesforce and sends an acknowledgement.</span></span> <span data-ttu-id="c70f4-172">在此步驟中，我們會建置在此協調流程，將查詢要求傳送到 Salesforce，以取得機會與相關的產品詳細資料，並接收回應。</span><span class="sxs-lookup"><span data-stu-id="c70f4-172">In this step, we build on this orchestration to send a query request to Salesforce to get product details related to the opportunity and receive a response.</span></span> <span data-ttu-id="c70f4-173">我們已在此步驟中建立的結構描述 （QueryRequest.xsd 和 QueryResult.xsd） 和我們將使用的訊息變數 （QueryRequestMsg 和 QueryResultMsg）。</span><span class="sxs-lookup"><span data-stu-id="c70f4-173">We have already created the schemas (QueryRequest.xsd and QueryResult.xsd) and the message variables (QueryRequestMsg and QueryResultMsg) that we’ll use in this step.</span></span>  
  
#### <a name="to-send-a-query-request-to-salesforce-and-receive-a-response"></a><span data-ttu-id="c70f4-174">若要將查詢要求傳送到 Salesforce 並接收回應</span><span class="sxs-lookup"><span data-stu-id="c70f4-174">To send a query request to Salesforce and receive a response</span></span>  
  
1. <span data-ttu-id="c70f4-175">新增 建構訊息 」 圖形之後**SendNotificationAck**圖形。</span><span class="sxs-lookup"><span data-stu-id="c70f4-175">Add a Construct Message shape after the **SendNotificationAck** shape.</span></span> <span data-ttu-id="c70f4-176">設定圖形的名稱`ConstructQuery`並設定**建構的訊息**屬性設**QueryRequestMsg**。</span><span class="sxs-lookup"><span data-stu-id="c70f4-176">Set the name of the shape to `ConstructQuery` and set the **Messages Constructed** property to **QueryRequestMsg**.</span></span>  
  
2. <span data-ttu-id="c70f4-177">內**ConstructQuery**圖形中新增**轉換**圖形。</span><span class="sxs-lookup"><span data-stu-id="c70f4-177">Within the **ConstructQuery** shape, add a **Transform** shape.</span></span> <span data-ttu-id="c70f4-178">按兩下以開啟 [轉換組態] 對話方塊中的 [轉換] 圖形。</span><span class="sxs-lookup"><span data-stu-id="c70f4-178">Double-click the Transform shape to open the Transform Configuration dialog box.</span></span> <span data-ttu-id="c70f4-179">在對話方塊中，選取**現有的對應**選項，然後再從下拉式清單選取**BtsSalesforceIntegration.Notification_QueryRequest**。</span><span class="sxs-lookup"><span data-stu-id="c70f4-179">In the dialog box, select the **Existing Map** option, and then from the drop-down select **BtsSalesforceIntegration.Notification_QueryRequest**.</span></span> <span data-ttu-id="c70f4-180">設定**來源**要**NotificaitonMessage**，**目的地**至**QueryRequestMsg**，然後按一下 **確定**.</span><span class="sxs-lookup"><span data-stu-id="c70f4-180">Set **Source** to **NotificaitonMessage**, **Destination** to **QueryRequestMsg**, and then click **OK**.</span></span>  
  
3. <span data-ttu-id="c70f4-181">內**ConstructQuery**圖形之後 轉換 圖形中，, 新增 訊息指派 」 圖形。</span><span class="sxs-lookup"><span data-stu-id="c70f4-181">Within the **ConstructQuery** shape, after the Transform shape, add a Message Assignment shape.</span></span> <span data-ttu-id="c70f4-182">按兩下訊息指派 」 圖形，並加入下列運算式：</span><span class="sxs-lookup"><span data-stu-id="c70f4-182">Double-click the Message Assignment shape and add the following expression:</span></span>  
  
   ```  
   QueryRequestMsg(BtsSalesforceIntegration.PropertySchema.Query) = QueryRequestMsg.Query;  
   ```  
  
    <span data-ttu-id="c70f4-183">如此一來，我們傳遞的值**查詢**中的項目**QueryRequestMsg**結構描述升級項目**查詢**屬性結構描述中。</span><span class="sxs-lookup"><span data-stu-id="c70f4-183">By doing this, we pass on the value of the **Query** element in the **QueryRequestMsg** schema to the promoted element **Query** in the property schema.</span></span> <span data-ttu-id="c70f4-184">在設定 Wcf-webhttp 連接埠時，我們將使用這個項目，以動態方式傳遞給要求訊息的查詢值。</span><span class="sxs-lookup"><span data-stu-id="c70f4-184">While configuring the WCF-WebHttp port, we’ll use this element to dynamically pass on the query value to the request message.</span></span>  
  
4. <span data-ttu-id="c70f4-185">在後**ConstructQuery**圖形中新增 「 傳送 」 圖形。</span><span class="sxs-lookup"><span data-stu-id="c70f4-185">After the **ConstructQuery** shape, add a Send shape.</span></span> <span data-ttu-id="c70f4-186">命名圖形`SendQueryRequest`並設定為訊息類型**QueryRequestMsg**。</span><span class="sxs-lookup"><span data-stu-id="c70f4-186">Name the shape `SendQueryRequest` and set the message type as **QueryRequestMsg**.</span></span>  
  
5. <span data-ttu-id="c70f4-187">在 [傳送] 圖形之後新增 「 接收 」 圖形並將它命名`ReceiveQueryResult`。</span><span class="sxs-lookup"><span data-stu-id="c70f4-187">After the Send shape, add a Receive shape and name it `ReceiveQueryResult`.</span></span> <span data-ttu-id="c70f4-188">設定圖形的訊息類型**QueryResultMsg**。</span><span class="sxs-lookup"><span data-stu-id="c70f4-188">Set the message type of the shape to **QueryResultMsg**.</span></span>  
  
6. <span data-ttu-id="c70f4-189">新增要將查詢要求傳送到 Salesforce 並接收回應的查詢結果的連接埠。</span><span class="sxs-lookup"><span data-stu-id="c70f4-189">Add a port to send query requests to Salesforce and receive the query result in response.</span></span> <span data-ttu-id="c70f4-190">在 [連接埠組態精靈] 中，選取下列選項：</span><span class="sxs-lookup"><span data-stu-id="c70f4-190">In the Port Configuration wizard, select the following options:</span></span>  
  
   - <span data-ttu-id="c70f4-191">將連接埠名稱指定為`SalesforceRESTInterface`。</span><span class="sxs-lookup"><span data-stu-id="c70f4-191">Specify the port name as `SalesforceRESTInterface`.</span></span>  
  
   - <span data-ttu-id="c70f4-192">選取 [建立新的連接埠類型] 選項。</span><span class="sxs-lookup"><span data-stu-id="c70f4-192">Select the option to create a new port type.</span></span>  
  
   - <span data-ttu-id="c70f4-193">設定**通訊模式**要*要求-回應*。</span><span class="sxs-lookup"><span data-stu-id="c70f4-193">Set **Communication Pattern** to *Request-Response*.</span></span>  
  
   - <span data-ttu-id="c70f4-194">設定**連接埠通訊方向**要*我會傳送要求並接收回應*並設定**連接埠繫結**至*指定更新*.</span><span class="sxs-lookup"><span data-stu-id="c70f4-194">Set **Port direction of communication** to *I’ll be sending a request and receiving a response* and set **Port binding** to *Specify later*.</span></span>  
  
     <span data-ttu-id="c70f4-195">連接**要求**作業的 「 傳送 」 圖形的連接埠 (*SendQueryRequest*) 和**回應**要 「 接收 」 圖形的連接埠的作業 (*ReceiveQueryResult*)。</span><span class="sxs-lookup"><span data-stu-id="c70f4-195">Connect the **Request** operation of port to the Send shape (*SendQueryRequest*) and the **Response** operation of the port to the Receive shape (*ReceiveQueryResult*).</span></span> <span data-ttu-id="c70f4-196">下列螢幕擷取畫面說明代表查詢要求傳送到 Salesforce 並接收回應的程序的協調流程的一部分。</span><span class="sxs-lookup"><span data-stu-id="c70f4-196">The following screenshot depicts the part of the orchestration that represents the process of sending the query request to Salesforce and receiving a response.</span></span>  
  
     <span data-ttu-id="c70f4-197">![將查詢傳送到 Salesforce 並接收回應](../core/media/bts-sf-sendqueryrequestorch.jpg "BTS_SF_SendQueryRequestOrch")</span><span class="sxs-lookup"><span data-stu-id="c70f4-197">![Send a query to Salesforce and receive response](../core/media/bts-sf-sendqueryrequestorch.jpg "BTS_SF_SendQueryRequestOrch")</span></span>  
  
   <span data-ttu-id="c70f4-198">本主題中，我們已更新協調流程以將查詢要求傳送到 Salesforce，而且接收更多詳細資料 （例如產品、 數量、 等等） 到有關 Salesforce 中建立的機會。</span><span class="sxs-lookup"><span data-stu-id="c70f4-198">In this topic, we updated the orchestration to send a query request to Salesforce and receive more details (such as products, quantity, etc.) about the opportunity that is created in Salesforce.</span></span> <span data-ttu-id="c70f4-199">在後續主題中，我們將會更新此解決方案的內部部署 SQL Server 資料庫中輸入 Salesforce 回應。</span><span class="sxs-lookup"><span data-stu-id="c70f4-199">In the subsequent topics, we will update this solution to enter the Salesforce response into an on-premise SQL Server database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c70f4-200">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c70f4-200">See Also</span></span>  
 [<span data-ttu-id="c70f4-201">步驟 3：在 Visual Studio 中建立 BizTalk Server 解決方案</span><span class="sxs-lookup"><span data-stu-id="c70f4-201">Step 3: Create the BizTalk Server Solution in Visual Studio</span></span>](../core/step-3-create-the-biztalk-server-solution-in-visual-studio.md)