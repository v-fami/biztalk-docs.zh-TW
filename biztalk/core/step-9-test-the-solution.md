---
title: 步驟 9： 測試方案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: df446ccc-add3-4dd3-b674-253dda385541
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 89a3722d6d8e1d4b730341dfaf16d60af1686f21
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25973068"
---
# <a name="step-9-test-the-solution"></a><span data-ttu-id="1b524-102">步驟 9： 測試方案</span><span class="sxs-lookup"><span data-stu-id="1b524-102">Step 9: Test the Solution</span></span>
<span data-ttu-id="1b524-103">本主題中，您可以測試混合式應用程式所傳送的 X12 840 銷售訂單訊息至 HTTP 端點部署 EDI 協議的位置。</span><span class="sxs-lookup"><span data-stu-id="1b524-103">In this topic you test the hybrid application by sending a X12 840 sales order message to the HTTP endpoint where the EDI agreement is deployed.</span></span> <span data-ttu-id="1b524-104">範例銷售訂單訊息看起來如下：</span><span class="sxs-lookup"><span data-stu-id="1b524-104">The sample sales order message looks like the following:</span></span>  
  
```  
ISA*00*          *00*          *ZZ*CONTOSO        *ZZ*NORTHWIND      *991221*1226*U*00401*000000025*0*T*:~  
GS*PO*THEM*US*19991221*1226*1*X*004010~  
ST*840*0002~  
BQT*00*BQT02*20120619*001*20120719~  
PER*1A*John*EM*John@contoso.com~  
N1*001~  
N2*co~  
N3*Contoso*One Contoso Way~  
N4*Redmond*WA*98052*US~  
PO1*PO101*121*01*10*AA*A1*1~  
CTT*475~  
SE*10*0002~  
GE*1*1~  
IEA*1*000000025~  
```  
  
 <span data-ttu-id="1b524-105">在此訊息中，反白顯示的區段 (行開頭**PO1**) 包含訂單數量。</span><span class="sxs-lookup"><span data-stu-id="1b524-105">In this message, the highlighted segment (the line starting with **PO1**) contains the order quantity.</span></span> <span data-ttu-id="1b524-106">此訊息中的訂單數量是*121*。</span><span class="sxs-lookup"><span data-stu-id="1b524-106">The order quantity in this message is *121*.</span></span> <span data-ttu-id="1b524-107">因此，如果您傳送此訊息，它必須插入**SalesOrder**資料表。</span><span class="sxs-lookup"><span data-stu-id="1b524-107">So, if you send this message, it must be inserted into the **SalesOrder** table.</span></span> <span data-ttu-id="1b524-108">您可以更新為小於 100 的數量，並重新傳送訊息，然後必須傳送至您在 FILE 傳送埠中指定的檔案位置。</span><span class="sxs-lookup"><span data-stu-id="1b524-108">You can update the quantity to less than 100 and resend the message, it must then be sent to the file location you specified in the FILE send port.</span></span>  
  
 <span data-ttu-id="1b524-109">若要將此訊息傳送至 EDI 協議，您可以使用**MessageSender**工具隨附的範例[!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1b524-109">To send this message to the EDI agreement, you can use the **MessageSender** tool shipped with the samples for [!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)].</span></span> <span data-ttu-id="1b524-110">您可以下載這些範例從[http://go.microsoft.com/fwlink/p/?LinkId=235057](http://go.microsoft.com/fwlink/p/?LinkId=235057)。</span><span class="sxs-lookup"><span data-stu-id="1b524-110">You can download the samples from [http://go.microsoft.com/fwlink/p/?LinkId=235057](http://go.microsoft.com/fwlink/p/?LinkId=235057).</span></span>  
  
### <a name="to-send-a-message"></a><span data-ttu-id="1b524-111">傳送訊息</span><span class="sxs-lookup"><span data-stu-id="1b524-111">To send a message</span></span>  
  
1.  <span data-ttu-id="1b524-112">找出**MessageSender**範例封裝中的專案並建置該檔案。</span><span class="sxs-lookup"><span data-stu-id="1b524-112">Locate the **MessageSender** project in the sample package and build it.</span></span>  
  
2.  <span data-ttu-id="1b524-113">使用產生**MessageSender**命令列可執行檔 （在專案的 \bin\Debug 資料夾） 下將訊息傳送至已部署 EDI 協議。</span><span class="sxs-lookup"><span data-stu-id="1b524-113">Use the resulting **MessageSender** command-line executable (under \bin\Debug folder within the project) to send messages to the deployed EDI agreement.</span></span> <span data-ttu-id="1b524-114">這項工具接受命令列參數，格式如下：</span><span class="sxs-lookup"><span data-stu-id="1b524-114">This tool accepts command-line parameter in the following format:</span></span>  
  
    ```  
    MessageSender.exe <ServiceBusNamespace> <IssuerName> <IssuerKey> <EDI agreement endpoint> <MessageFilepath> <ContentType>  
    ```  
  
     <span data-ttu-id="1b524-115">其中，</span><span class="sxs-lookup"><span data-stu-id="1b524-115">Where,</span></span>  
  
    |<span data-ttu-id="1b524-116">參數名稱</span><span class="sxs-lookup"><span data-stu-id="1b524-116">Parameter name</span></span>|<span data-ttu-id="1b524-117">Description</span><span class="sxs-lookup"><span data-stu-id="1b524-117">Description</span></span>|  
    |--------------------|-----------------|  
    |<span data-ttu-id="1b524-118">ServiceBusNamespace</span><span class="sxs-lookup"><span data-stu-id="1b524-118">ServiceBusNamespace</span></span>|<span data-ttu-id="1b524-119">服務匯流排命名空間</span><span class="sxs-lookup"><span data-stu-id="1b524-119">The Service Bus namespace</span></span>|  
    |<span data-ttu-id="1b524-120">IssuerName</span><span class="sxs-lookup"><span data-stu-id="1b524-120">IssuerName</span></span>|<span data-ttu-id="1b524-121">指定的命名空間的簽發者名稱</span><span class="sxs-lookup"><span data-stu-id="1b524-121">Issuer Name for the specified namespace</span></span>|  
    |<span data-ttu-id="1b524-122">IssuerKey</span><span class="sxs-lookup"><span data-stu-id="1b524-122">IssuerKey</span></span>|<span data-ttu-id="1b524-123">指定的命名空間的簽發者金鑰</span><span class="sxs-lookup"><span data-stu-id="1b524-123">Issuer Key for the specified namespace</span></span>|  
    |<span data-ttu-id="1b524-124">EDI 協議端點</span><span class="sxs-lookup"><span data-stu-id="1b524-124">EDI agreement endpoint</span></span>|<span data-ttu-id="1b524-125">部署 EDI 協議的所在端點。</span><span class="sxs-lookup"><span data-stu-id="1b524-125">The endpoint where the EDI agreement is deployed.</span></span> <span data-ttu-id="1b524-126">您可以取得此端點 URL，從 [接收設定] 索引標籤 （並在其中傳輸頁面） 的部署在 EDI 協議[(Azure) 的步驟 2： 建立 EDI 協議](../core/step-2-for-azure-create-an-edi-agreement.md)。</span><span class="sxs-lookup"><span data-stu-id="1b524-126">You can get this endpoint URL from the Receive Settings tab (and within that, the Transport page) of the EDI agreement you deployed in [Step 2 (For Azure): Create an EDI Agreement](../core/step-2-for-azure-create-an-edi-agreement.md).</span></span>|  
    |<span data-ttu-id="1b524-127">MessageFilePath</span><span class="sxs-lookup"><span data-stu-id="1b524-127">MessageFilePath</span></span>|<span data-ttu-id="1b524-128">包含範例要求訊息的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="1b524-128">Path to the file that contains the sample request message.</span></span>|  
    |<span data-ttu-id="1b524-129">ContentType</span><span class="sxs-lookup"><span data-stu-id="1b524-129">ContentType</span></span>|<span data-ttu-id="1b524-130">本教學課程，請將此參數設定為**text/plain**。</span><span class="sxs-lookup"><span data-stu-id="1b524-130">For this tutorial, set this parameter to **text/plain**.</span></span>|  
  
     <span data-ttu-id="1b524-131">開啟命令提示字元並瀏覽至您建置的方案**MessageSender**專案。</span><span class="sxs-lookup"><span data-stu-id="1b524-131">Open a command prompt and navigate to the solution where you built the **MessageSender** project.</span></span> <span data-ttu-id="1b524-132">執行下列命令，以傳送具有大於 100 的訂單數量的要求訊息：</span><span class="sxs-lookup"><span data-stu-id="1b524-132">Run the following command to send the request message with order quantity more than 100:</span></span>  
  
    ```  
    MessageSender.exe <service bus namespace> owner <issuer key>https://<namespace>.servicebus.appfabriclabs.com/7576ff3d-a0f3-4a46-a4f6-f5be4a50616a/DemoAgreement<path to the sample message> "text/plain"  
    ```  
  
3.  <span data-ttu-id="1b524-133">開啟 SQL Server Management Studio 中，連接到資料庫，其中包含**SalesOrder**資料表，並確認新記錄插入資料表。</span><span class="sxs-lookup"><span data-stu-id="1b524-133">Open SQL Server Management Studio, connect to the database that contains the **SalesOrder** table, and verify that a new record is inserted into the table.</span></span> <span data-ttu-id="1b524-134">中的值會注意到**Qty**資料行; 它必須是*121*。</span><span class="sxs-lookup"><span data-stu-id="1b524-134">Notice the value in the **Qty** column; it must be *121*.</span></span>  
  
4.  <span data-ttu-id="1b524-135">使用**MessageSender**傳送另一則訊息，但這次設定的數量值已排序訊息中*99*。</span><span class="sxs-lookup"><span data-stu-id="1b524-135">Use **MessageSender** to send another message, but this time set the value of the quantity ordered in the message to *99*.</span></span> <span data-ttu-id="1b524-136">您會注意到現在，沒有記錄插入在**SalesOrder**資料表。</span><span class="sxs-lookup"><span data-stu-id="1b524-136">You will notice that now, no record is inserted in the **SalesOrder** table.</span></span> <span data-ttu-id="1b524-137">相反地，訊息會複製到您指定用於接收訊息的訂單數量小於 100 的檔案位置。</span><span class="sxs-lookup"><span data-stu-id="1b524-137">Instead, the message is copied to the file location you specified for receiving messages with order quantity less than 100.</span></span> <span data-ttu-id="1b524-138">收到的訊息如下所示：</span><span class="sxs-lookup"><span data-stu-id="1b524-138">The received message resembles the following:</span></span>  
  
    ```  
    <ns1:SalesOrder xmlns:ns0="http://schemas.microsoft.com/BizTalk/EDI/X12/2006" xmlns:ns1="http://ECommerceSalesOrder.Inbound">  
      <CompanyCode>co</CompanyCode>  
      <PartID>1</PartID>  
      <Quantity>99</Quantity>  
      <AskPrice>10</AskPrice>  
      <RequestShipmentDate>2012-07-19</RequestShipmentDate>  
      <Address>  
        <Line1>Contoso</Line1>  
        <Line2>One Contoso Way</Line2>  
        <City>Redmond</City>  
        <State>WA</State>  
        <Country>US</Country>  
        <Zipcode>98052</Zipcode>  
      </Address>  
      <Contact>  
        <Firstname>John</Firstname>  
        <Lastname>John@contoso.com</Lastname>  
      </Contact>  
      <Comments>Order from Partnerco</Comments>  
      <DateNow>2012-06-19</DateNow>  
    </ns1:SalesOrder>  
  
    ```  
  
     <span data-ttu-id="1b524-139">中的值會注意到**數量**項目。</span><span class="sxs-lookup"><span data-stu-id="1b524-139">Notice the value in the **Quantity** element.</span></span> <span data-ttu-id="1b524-140">它是*99*。</span><span class="sxs-lookup"><span data-stu-id="1b524-140">It is *99*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b524-141">請參閱</span><span class="sxs-lookup"><span data-stu-id="1b524-141">See Also</span></span>  
 [<span data-ttu-id="1b524-142">教學課程 4： 建立使用 BizTalk Server 2013 的混合式應用程式</span><span class="sxs-lookup"><span data-stu-id="1b524-142">Tutorial 4: Creating a Hybrid Application Using BizTalk Server 2013</span></span>](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)