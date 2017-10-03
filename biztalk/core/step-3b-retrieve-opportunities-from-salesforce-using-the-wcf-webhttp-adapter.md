---
title: "步驟 3b： 擷取商機的詳細資料來自使用 Wcf-webhttp 配接器的 Salesforce |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 115c908f-777b-4c51-85ea-71d639b01775
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 05312890d7cd21810651e7e41a8418080912f72f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3b-retrieve-opportunity-details-from-salesforce-using-the-wcf-webhttp-adapter"></a><span data-ttu-id="71910-102">步驟 3b： 擷取來自 Salesforce 使用 Wcf-webhttp 配接器的機會詳細資料</span><span class="sxs-lookup"><span data-stu-id="71910-102">Step 3b: Retrieve Opportunity Details from Salesforce using the WCF-WebHttp Adapter</span></span>
<span data-ttu-id="71910-103">在本節中，我們會著重於處理內送商機通知的協調流程、從通知擷取商機名稱，並用來建立要求查詢以傳送至 Salesforce。</span><span class="sxs-lookup"><span data-stu-id="71910-103">In this section, we’ll enhance the orchestration to process the incoming opportunity notification, extract the opportunity name from the notification, and use that to create a request query to send to Salesforce.</span></span> <span data-ttu-id="71910-104">這樣會擷取與商機關聯的產品相關特定詳細資料。</span><span class="sxs-lookup"><span data-stu-id="71910-104">This retrieves specific details about the products associated with the opportunity.</span></span> <span data-ttu-id="71910-105">來自 Salesforce 的查詢回應會由 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收。</span><span class="sxs-lookup"><span data-stu-id="71910-105">The query response from Salesforce is received back into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="71910-106">若要達到此目標，我們會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="71910-106">To achieve this, we’ll perform the following steps:</span></span>  
  
-   <span data-ttu-id="71910-107">建立結構描述和訊息變數以傳送查詢訊息至 Salesforce。</span><span class="sxs-lookup"><span data-stu-id="71910-107">Create a schema and message variables to send a query message to Salesforce.</span></span>  
  
-   <span data-ttu-id="71910-108">建立對應以使用商機通知中的值來建立查詢以擷取與該商機相關聯的產品詳細資料。</span><span class="sxs-lookup"><span data-stu-id="71910-108">Create a map to use the values from the opportunity notification for creating a query to retrieve product details associated with the opportunity.</span></span>  
  
-   <span data-ttu-id="71910-109">建立結構描述以接收來自 Salesforce 的查詢回應。</span><span class="sxs-lookup"><span data-stu-id="71910-109">Create a schema to receive a query response from Salesforce.</span></span>  
  
-   <span data-ttu-id="71910-110">為要求和回應結構描述建立訊息變數。</span><span class="sxs-lookup"><span data-stu-id="71910-110">Create message variables for the request and response schemas.</span></span>  
  
## <a name="create-schema-and-message-variables-to-send-query-messages-to-salesforce"></a><span data-ttu-id="71910-111">建立結構描述和訊息變數，以傳送查詢訊息至 Salesforce</span><span class="sxs-lookup"><span data-stu-id="71910-111">Create Schema and Message Variables to Send Query Messages to Salesforce</span></span>  
 <span data-ttu-id="71910-112">若要擷取來自 Salesforce 的產品詳細資料，使用可透過商機通知的資訊，我們需要傳送查詢到 Salesforce。</span><span class="sxs-lookup"><span data-stu-id="71910-112">To retrieve product details from Salesforce by using the information available through an Opportunity notification, we need to send a query to Salesforce.</span></span> <span data-ttu-id="71910-113">查詢會以 XML 訊息傳送至 Salesforce。</span><span class="sxs-lookup"><span data-stu-id="71910-113">The query is sent to Salesforce as an XML message.</span></span> <span data-ttu-id="71910-114">因此，在下列程序建立要求訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="71910-114">So, in the following procedure we create a schema for the request message.</span></span> <span data-ttu-id="71910-115">在後續的程序，我們會將對應的商機通知的結構描述與此結構描述來建構查詢來擷取產品詳細資料的機會。</span><span class="sxs-lookup"><span data-stu-id="71910-115">In the subsequent procedure, we will map the opportunity notification schema with this schema to construct a query for retrieving product details for the opportunity.</span></span>  
  
#### <a name="to-create-a-schema-for-sending-query-request"></a><span data-ttu-id="71910-116">若要建立查詢要求傳送的結構描述</span><span class="sxs-lookup"><span data-stu-id="71910-116">To create a schema for sending query request</span></span>  
  
1.  <span data-ttu-id="71910-117">加入新的結構描述[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案。</span><span class="sxs-lookup"><span data-stu-id="71910-117">Add a new schema to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.</span></span> <span data-ttu-id="71910-118">將它命名為 `QueryRequest.xsd`。</span><span class="sxs-lookup"><span data-stu-id="71910-118">Name it `QueryRequest.xsd`.</span></span>  
  
2.  <span data-ttu-id="71910-119">重新命名的根節點`QueryRequest`。</span><span class="sxs-lookup"><span data-stu-id="71910-119">Rename the root node to `QueryRequest`.</span></span> <span data-ttu-id="71910-120">新增 QueryRequest 記錄下的子欄位項目並將其命名`Query`。</span><span class="sxs-lookup"><span data-stu-id="71910-120">Add a child field element under the QueryRequest record and name it `Query`.</span></span>  
  
3.  <span data-ttu-id="71910-121">升級**查詢**，使其可供協調流程中使用的結構描述中的項目。</span><span class="sxs-lookup"><span data-stu-id="71910-121">Promote the **Query** element in the schema so that it is available for use within the orchestration.</span></span> <span data-ttu-id="71910-122">在接下來的步驟中，我們將使用此升級的項目來將查詢字串指定。</span><span class="sxs-lookup"><span data-stu-id="71910-122">In the later steps we will use this promoted element to assign the query string.</span></span>  
  
     <span data-ttu-id="71910-123">以滑鼠右鍵按一下**查詢**項目，指向**升階**，然後按一下 **快速升級**。</span><span class="sxs-lookup"><span data-stu-id="71910-123">Right-click the **Query** element, point to **Promote**, and then click **Quick Promotions**.</span></span> <span data-ttu-id="71910-124">這會導致建立**PropertySchema.xsd**結構描述與**查詢**項目。</span><span class="sxs-lookup"><span data-stu-id="71910-124">This results in creating a **PropertySchema.xsd** schema with a **Query** element.</span></span> <span data-ttu-id="71910-125">請注意命名空間，如 PropertySchema。</span><span class="sxs-lookup"><span data-stu-id="71910-125">Note the namespace for the PropertySchema.</span></span> <span data-ttu-id="71910-126">您必須在未來此步驟時設定中的實體連接埠[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="71910-126">You will need this in the future steps while configuring the physical ports in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
4.  <span data-ttu-id="71910-127">儲存所有變更。</span><span class="sxs-lookup"><span data-stu-id="71910-127">Save all changes.</span></span>  
  
## <a name="map-the-opportunity-notification-schema-to-the-query-schema"></a><span data-ttu-id="71910-128">將有機會通知結構描述對應至查詢的結構描述</span><span class="sxs-lookup"><span data-stu-id="71910-128">Map the Opportunity Notification Schema to the Query Schema</span></span>  
 <span data-ttu-id="71910-129">若要擷取與該商機相關聯的產品詳細資料，我們需要與下列類似的查詢傳送至 Salesforce:</span><span class="sxs-lookup"><span data-stu-id="71910-129">To retrieve the product details associated with the opportunity, we need to send a query similar to the following to Salesforce:</span></span>  
  
```  
SELECT Amount, Id, Name,(SELECT Quantity, ListPrice, PricebookEntry.UnitPrice, PricebookEntry.Name FROM OpportunityLineItems) FROM Opportunity Where Name = '<opportunity_name>'  
```  
  
 <span data-ttu-id="71910-130">在上一個程序中我們已經建立查詢訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="71910-130">In the previous procedure we already created the schema of the query message.</span></span> <span data-ttu-id="71910-131">在此程序中，我們商機通知結構描述對應至查詢要求結構描述，並使用運算質來建構這個查詢。</span><span class="sxs-lookup"><span data-stu-id="71910-131">In this procedure, we map the opportunity notification schema to the query request schema and use functoids to construct this query.</span></span> <span data-ttu-id="71910-132">此查詢會當做值傳遞給**查詢**中的項目**QueryRequest.xsd**結構描述。</span><span class="sxs-lookup"><span data-stu-id="71910-132">This query will be passed as a value to the **Query** element in the **QueryRequest.xsd** schema.</span></span>  
  
#### <a name="to-map-the-opportunity-notification"></a><span data-ttu-id="71910-133">若要將對應商機通知</span><span class="sxs-lookup"><span data-stu-id="71910-133">To map the opportunity notification</span></span>  
  
1.  <span data-ttu-id="71910-134">新增對應到[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案。</span><span class="sxs-lookup"><span data-stu-id="71910-134">Add a map to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.</span></span> <span data-ttu-id="71910-135">Map 命名`Notification_QueryRequest.btm`。</span><span class="sxs-lookup"><span data-stu-id="71910-135">Name the map `Notification_QueryRequest.btm`.</span></span>  
  
2.  <span data-ttu-id="71910-136">將來源結構描述設**NotificationService_soap_sforce_com_2005_09_outbound.xsd**。</span><span class="sxs-lookup"><span data-stu-id="71910-136">Set the source schema to **NotificationService_soap_sforce_com_2005_09_outbound.xsd**.</span></span> <span data-ttu-id="71910-137">將目的結構描述設**QueryRequest**.xsd。</span><span class="sxs-lookup"><span data-stu-id="71910-137">Set the destination schema to **QueryRequest**.xsd.</span></span>  
  
3.  <span data-ttu-id="71910-138">新增**字串串連**運算質至對應的介面。</span><span class="sxs-lookup"><span data-stu-id="71910-138">Add a **String Concatenate** functoid to the mapping surface.</span></span> <span data-ttu-id="71910-139">開啟**設定字串串連運算質**對話方塊指定的輸入的值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="71910-139">Open the **Configure String Concatenate Functoid** dialog box and specify the input values as follows:</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="71910-140">Input [0]</span><span class="sxs-lookup"><span data-stu-id="71910-140">Input[0]</span></span>|<span data-ttu-id="71910-141">選取量、 識別碼、 名稱 (選取 Quantity、 ListPrice PricebookEntry.UnitPrice，PricebookEntry.Name 從 OpportunityLineItems) 從有機會 Where Name = '</span><span class="sxs-lookup"><span data-stu-id="71910-141">SELECT Amount, Id, Name,(SELECT Quantity, ListPrice, PricebookEntry.UnitPrice, PricebookEntry.Name FROM OpportunityLineItems) FROM Opportunity Where Name = '</span></span>|  
    |<span data-ttu-id="71910-142">Input [1]</span><span class="sxs-lookup"><span data-stu-id="71910-142">Input[1]</span></span>|<span data-ttu-id="71910-143">若要使用名稱元素的值做為第二個輸入的運算質連接來源結構描述中的名稱項目。</span><span class="sxs-lookup"><span data-stu-id="71910-143">Connect the Name element in the source schema to the functoid to use the value of the Name element as the second input.</span></span>|  
    |<span data-ttu-id="71910-144">輸入 [2]</span><span class="sxs-lookup"><span data-stu-id="71910-144">Input[2]</span></span>|<span data-ttu-id="71910-145">'**附註：**最後一個的輸入值，指定只右單引號 （'）。</span><span class="sxs-lookup"><span data-stu-id="71910-145">' **Note:**  For the last input value, specify only a closing single quote (').</span></span>|  
  
     <span data-ttu-id="71910-146">下列螢幕擷取畫面說明的組態**字串串連**運算質。</span><span class="sxs-lookup"><span data-stu-id="71910-146">The following screenshot depicts the configuration for the **String Concatenate** functoid.</span></span>  
  
     <span data-ttu-id="71910-147">![設定字串串連運算質](../core/media/bts-sf-stringconcatenate.jpg "BTS_SF_StringConcatenate")</span><span class="sxs-lookup"><span data-stu-id="71910-147">![Configure String Concatenate functoid](../core/media/bts-sf-stringconcatenate.jpg "BTS_SF_StringConcatenate")</span></span>  
  
     <span data-ttu-id="71910-148">當串連三個輸入的參數時，它將會形成所需的查詢傳送至 Salesforce。</span><span class="sxs-lookup"><span data-stu-id="71910-148">When the three input parameters are concatenated, it will form the required query to be sent to Salesforce.</span></span>  
  
4.  <span data-ttu-id="71910-149">連接字串串連運算質至目的結構描述中的查詢項目，如下列螢幕擷取畫面所示。</span><span class="sxs-lookup"><span data-stu-id="71910-149">Connect the String Concatenate functoid to the Query element in the destination schema, as shown in the following screenshot.</span></span>  
  
     <span data-ttu-id="71910-150">![對應至查詢的結構描述的通知回應](../core/media/bts-sf-notification-query-mapping.jpg "BTS_SF_Notification_Query_Mapping")</span><span class="sxs-lookup"><span data-stu-id="71910-150">![Map notification response to query schema](../core/media/bts-sf-notification-query-mapping.jpg "BTS_SF_Notification_Query_Mapping")</span></span>  
  
5.  <span data-ttu-id="71910-151">將變更儲存到對應。</span><span class="sxs-lookup"><span data-stu-id="71910-151">Save changes to the map.</span></span>  
  
## <a name="creating-schema-to-receive-the-query-response-message"></a><span data-ttu-id="71910-152">建立用來接收查詢回應訊息的結構描述</span><span class="sxs-lookup"><span data-stu-id="71910-152">Creating Schema to Receive the Query Response Message</span></span>  
 <span data-ttu-id="71910-153">在本節中，我們會建立要接收來自 Salesforce 的查詢回應訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="71910-153">In this section, we create the schema to receive the query response message from Salesforce.</span></span> <span data-ttu-id="71910-154">在本節中，我們可以手動建立查詢回應結構的描述。</span><span class="sxs-lookup"><span data-stu-id="71910-154">In this section, we manually create the schema for the query response.</span></span>  
  
#### <a name="to-create-a-schema-to-receive-the-query-response"></a><span data-ttu-id="71910-155">若要建立接收查詢回應結構描述</span><span class="sxs-lookup"><span data-stu-id="71910-155">To create a schema to receive the query response</span></span>  
  
1.  <span data-ttu-id="71910-156">加入新的結構描述[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案，並命名`QueryResult.xsd`。</span><span class="sxs-lookup"><span data-stu-id="71910-156">Add a new schema to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project and name it `QueryResult.xsd`.</span></span>  
  
2.  <span data-ttu-id="71910-157">Salesforce [QueryResult](http://go.microsoft.com/fwlink/?LinkId=287017)物件描述接收來自 Salesforce 的查詢回應。</span><span class="sxs-lookup"><span data-stu-id="71910-157">The Salesforce [QueryResult](http://go.microsoft.com/fwlink/?LinkId=287017) object depicts the query response received from Salesforce.</span></span> <span data-ttu-id="71910-158">因此，我們會建置結構描述來描述下列：</span><span class="sxs-lookup"><span data-stu-id="71910-158">So, we’ll build a schema to depict the following:</span></span>  
  
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
  
     <span data-ttu-id="71910-159">結構描述結構看起來應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="71910-159">The schema structure should look like the following:</span></span>  
  
     <span data-ttu-id="71910-160">![來自 Salesforce 的查詢回應結構描述](../core/media/bts-sf-queryresult.jpg "BTS_SF_QueryResult")</span><span class="sxs-lookup"><span data-stu-id="71910-160">![Schema for query response from Salesforce](../core/media/bts-sf-queryresult.jpg "BTS_SF_QueryResult")</span></span>  
  
3.  <span data-ttu-id="71910-161">將變更儲存至結構描述。</span><span class="sxs-lookup"><span data-stu-id="71910-161">Save changes to the schema.</span></span>  
  
## <a name="create-message-variables-for-queryrequest-and-queryresult-schemas"></a><span data-ttu-id="71910-162">建立訊息變數 QueryRequest 和 QueryResult 結構描述</span><span class="sxs-lookup"><span data-stu-id="71910-162">Create Message Variables for QueryRequest and QueryResult Schemas</span></span>  
 <span data-ttu-id="71910-163">您已建立的 QueryRequest 與 QueryResult 結構描述之後，您必須建立兩個訊息變數來代表兩個訊息類型的協調流程中。</span><span class="sxs-lookup"><span data-stu-id="71910-163">After you have created the QueryRequest and QueryResult schemas, you must create two message variables in the orchestration to represent the two message types.</span></span>  
  
#### <a name="to-create-message-variables"></a><span data-ttu-id="71910-164">建立訊息變數</span><span class="sxs-lookup"><span data-stu-id="71910-164">To create message variables</span></span>  
  
1.  <span data-ttu-id="71910-165">開啟**NotificationService.odx**協調流程，在 [協調流程] 檢視中，加入兩個新的訊息。</span><span class="sxs-lookup"><span data-stu-id="71910-165">Open the **NotificationService.odx** orchestration and in the orchestration view, add two new messages.</span></span> <span data-ttu-id="71910-166">設定訊息名稱，做為`QueryRequestMsg`和`QueryResultMsg`。</span><span class="sxs-lookup"><span data-stu-id="71910-166">Set the message names as `QueryRequestMsg` and `QueryResultMsg`.</span></span>  
  
2.  <span data-ttu-id="71910-167">設定訊息類型**QueryRequestMsg**為**BtsSalesforceIntegration.QueryRequest**。</span><span class="sxs-lookup"><span data-stu-id="71910-167">Set the message type for **QueryRequestMsg** as **BtsSalesforceIntegration.QueryRequest**.</span></span>  
  
3.  <span data-ttu-id="71910-168">設定訊息類型**QueryResultMsg**為**BtsSalesforceIntegration.QueryResult**。</span><span class="sxs-lookup"><span data-stu-id="71910-168">Set the message type for **QueryResultMsg** as **BtsSalesforceIntegration.QueryResult**.</span></span>  
  
4.  <span data-ttu-id="71910-169">將變更儲存至協調流程。</span><span class="sxs-lookup"><span data-stu-id="71910-169">Save changes to the orchestration.</span></span>  
  
## <a name="update-the-orchestration-to-send-message-to-salesforce-and-receive-a-response"></a><span data-ttu-id="71910-170">更新協調流程以傳送訊息至 Salesforce 並接收回應</span><span class="sxs-lookup"><span data-stu-id="71910-170">Update the Orchestration to Send Message to Salesforce and Receive a Response</span></span>  
 <span data-ttu-id="71910-171">主題中的 <<c0> [ 步驟 3a： 到 BizTalk Server 接收 Salesforce 商機通知](../core/step-3a-receive-salesforce-opportunity-notification-into-biztalk-server.md)，我們建立了協調流程接收來自 Salesforce 的商機通知和傳送通知。</span><span class="sxs-lookup"><span data-stu-id="71910-171">In the topic [Step 3a: Receive Salesforce Opportunity Notification into BizTalk Server](../core/step-3a-receive-salesforce-opportunity-notification-into-biztalk-server.md), we built the orchestration that receives opportunity notifications from Salesforce and sends an acknowledgement.</span></span> <span data-ttu-id="71910-172">在此步驟中，我們會建置此協調流程將查詢要求傳送至 Salesforce 以取得商機相關的產品詳細資料，並接收回應。</span><span class="sxs-lookup"><span data-stu-id="71910-172">In this step, we build on this orchestration to send a query request to Salesforce to get product details related to the opportunity and receive a response.</span></span> <span data-ttu-id="71910-173">我們已經在此步驟中建立的結構描述 （QueryRequest.xsd 和 QueryResult.xsd） 和我們將使用的訊息變數 （QueryRequestMsg 和 QueryResultMsg）。</span><span class="sxs-lookup"><span data-stu-id="71910-173">We have already created the schemas (QueryRequest.xsd and QueryResult.xsd) and the message variables (QueryRequestMsg and QueryResultMsg) that we’ll use in this step.</span></span>  
  
#### <a name="to-send-a-query-request-to-salesforce-and-receive-a-response"></a><span data-ttu-id="71910-174">以查詢要求傳送至 Salesforce 並接收回應</span><span class="sxs-lookup"><span data-stu-id="71910-174">To send a query request to Salesforce and receive a response</span></span>  
  
1.  <span data-ttu-id="71910-175">新增 建構訊息 」 圖形之後**SendNotificationAck**圖形。</span><span class="sxs-lookup"><span data-stu-id="71910-175">Add a Construct Message shape after the **SendNotificationAck** shape.</span></span> <span data-ttu-id="71910-176">設定圖形的名稱`ConstructQuery`並設定**建構的訊息**屬性**QueryRequestMsg**。</span><span class="sxs-lookup"><span data-stu-id="71910-176">Set the name of the shape to `ConstructQuery` and set the **Messages Constructed** property to **QueryRequestMsg**.</span></span>  
  
2.  <span data-ttu-id="71910-177">內**ConstructQuery**圖形中新增**轉換**圖形。</span><span class="sxs-lookup"><span data-stu-id="71910-177">Within the **ConstructQuery** shape, add a **Transform** shape.</span></span> <span data-ttu-id="71910-178">按兩下以開啟 [轉換組態] 對話方塊的 [轉換] 圖形。</span><span class="sxs-lookup"><span data-stu-id="71910-178">Double-click the Transform shape to open the Transform Configuration dialog box.</span></span> <span data-ttu-id="71910-179">在對話方塊中，選取**現有對應**選項，然後再從下拉式清單選取**BtsSalesforceIntegration.Notification_QueryRequest**。</span><span class="sxs-lookup"><span data-stu-id="71910-179">In the dialog box, select the **Existing Map** option, and then from the drop-down select **BtsSalesforceIntegration.Notification_QueryRequest**.</span></span> <span data-ttu-id="71910-180">設定**來源**至**NotificaitonMessage**，**目的地**至**QueryRequestMsg**，然後按一下 **確定**.</span><span class="sxs-lookup"><span data-stu-id="71910-180">Set **Source** to **NotificaitonMessage**, **Destination** to **QueryRequestMsg**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="71910-181">內**ConstructQuery**圖形，在 [轉換] 圖形之後新增 「 訊息指派 」 圖形。</span><span class="sxs-lookup"><span data-stu-id="71910-181">Within the **ConstructQuery** shape, after the Transform shape, add a Message Assignment shape.</span></span> <span data-ttu-id="71910-182">按兩下訊息指派 」 圖形，並加入下列運算式：</span><span class="sxs-lookup"><span data-stu-id="71910-182">Double-click the Message Assignment shape and add the following expression:</span></span>  
  
    ```  
    QueryRequestMsg(BtsSalesforceIntegration.PropertySchema.Query) = QueryRequestMsg.Query;  
    ```  
  
     <span data-ttu-id="71910-183">如此一來，我們傳遞的值為**查詢**中的項目**QueryRequestMsg**結構描述升級項目**查詢**屬性結構描述中。</span><span class="sxs-lookup"><span data-stu-id="71910-183">By doing this, we pass on the value of the **Query** element in the **QueryRequestMsg** schema to the promoted element **Query** in the property schema.</span></span> <span data-ttu-id="71910-184">在設定 Wcf-webhttp 連接埠時，我們會使用這個項目，以動態方式將傳遞查詢值給要求訊息。</span><span class="sxs-lookup"><span data-stu-id="71910-184">While configuring the WCF-WebHttp port, we’ll use this element to dynamically pass on the query value to the request message.</span></span>  
  
4.  <span data-ttu-id="71910-185">之後**ConstructQuery**圖形中新增 「 傳送 」 圖形。</span><span class="sxs-lookup"><span data-stu-id="71910-185">After the **ConstructQuery** shape, add a Send shape.</span></span> <span data-ttu-id="71910-186">命名圖形`SendQueryRequest`並將訊息類型做為**QueryRequestMsg**。</span><span class="sxs-lookup"><span data-stu-id="71910-186">Name the shape `SendQueryRequest` and set the message type as **QueryRequestMsg**.</span></span>  
  
5.  <span data-ttu-id="71910-187">在 [傳送] 圖形之後新增 「 接收 」 圖形並將它命名`ReceiveQueryResult`。</span><span class="sxs-lookup"><span data-stu-id="71910-187">After the Send shape, add a Receive shape and name it `ReceiveQueryResult`.</span></span> <span data-ttu-id="71910-188">設定圖形的訊息類型**QueryResultMsg**。</span><span class="sxs-lookup"><span data-stu-id="71910-188">Set the message type of the shape to **QueryResultMsg**.</span></span>  
  
6.  <span data-ttu-id="71910-189">新增連接埠來傳送至 Salesforce 的查詢要求並接收回應的查詢結果。</span><span class="sxs-lookup"><span data-stu-id="71910-189">Add a port to send query requests to Salesforce and receive the query result in response.</span></span> <span data-ttu-id="71910-190">在連接埠組態精靈中，選取下列選項：</span><span class="sxs-lookup"><span data-stu-id="71910-190">In the Port Configuration wizard, select the following options:</span></span>  
  
    -   <span data-ttu-id="71910-191">將連接埠名稱指定為`SalesforceRESTInterface`。</span><span class="sxs-lookup"><span data-stu-id="71910-191">Specify the port name as `SalesforceRESTInterface`.</span></span>  
  
    -   <span data-ttu-id="71910-192">選取 建立新的連接埠類型。</span><span class="sxs-lookup"><span data-stu-id="71910-192">Select the option to create a new port type.</span></span>  
  
    -   <span data-ttu-id="71910-193">設定**通訊模式**至*要求-回應*。</span><span class="sxs-lookup"><span data-stu-id="71910-193">Set **Communication Pattern** to *Request-Response*.</span></span>  
  
    -   <span data-ttu-id="71910-194">設定**連接埠通訊方向**至*我要傳送要求並接收回應*並設定**連接埠繫結**至*指定更新*.</span><span class="sxs-lookup"><span data-stu-id="71910-194">Set **Port direction of communication** to *I’ll be sending a request and receiving a response* and set **Port binding** to *Specify later*.</span></span>  
  
     <span data-ttu-id="71910-195">連接**要求**「 傳送 」 圖形的連接埠的作業 (*SendQueryRequest*) 和**回應**作業的 「 接收 」 圖形的連接埠 (*ReceiveQueryResult*)。</span><span class="sxs-lookup"><span data-stu-id="71910-195">Connect the **Request** operation of port to the Send shape (*SendQueryRequest*) and the **Response** operation of the port to the Receive shape (*ReceiveQueryResult*).</span></span> <span data-ttu-id="71910-196">下列螢幕擷取畫面說明代表查詢要求傳送到 Salesforce 並接收回應的程序的協調流程的一部分。</span><span class="sxs-lookup"><span data-stu-id="71910-196">The following screenshot depicts the part of the orchestration that represents the process of sending the query request to Salesforce and receiving a response.</span></span>  
  
     <span data-ttu-id="71910-197">![傳送查詢到 Salesforce 並接收回應](../core/media/bts-sf-sendqueryrequestorch.jpg "BTS_SF_SendQueryRequestOrch")</span><span class="sxs-lookup"><span data-stu-id="71910-197">![Send a query to Salesforce and receive response](../core/media/bts-sf-sendqueryrequestorch.jpg "BTS_SF_SendQueryRequestOrch")</span></span>  
  
 <span data-ttu-id="71910-198">本主題中，我們已更新的協調流程傳送至 Salesforce 的查詢要求和接收到有關有機會在 Salesforce 中建立更多詳細資料 （例如產品、 數量、 等等）。</span><span class="sxs-lookup"><span data-stu-id="71910-198">In this topic, we updated the orchestration to send a query request to Salesforce and receive more details (such as products, quantity, etc.) about the opportunity that is created in Salesforce.</span></span> <span data-ttu-id="71910-199">在後續主題中，我們將會更新此解決方案，以在內部部署 SQL Server 資料庫中輸入 Salesforce 回應。</span><span class="sxs-lookup"><span data-stu-id="71910-199">In the subsequent topics, we will update this solution to enter the Salesforce response into an on-premise SQL Server database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71910-200">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71910-200">See Also</span></span>  
 [<span data-ttu-id="71910-201">步驟 3： 建立 Visual Studio 中的 BizTalk Server 解決方案</span><span class="sxs-lookup"><span data-stu-id="71910-201">Step 3: Create the BizTalk Server Solution in Visual Studio</span></span>](../core/step-3-create-the-biztalk-server-solution-in-visual-studio.md)