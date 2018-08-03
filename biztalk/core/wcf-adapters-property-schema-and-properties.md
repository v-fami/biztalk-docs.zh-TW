---
title: WCF 配接器屬性結構描述和屬性 |Microsoft 文件
ms.custom: ''
ms.date: 02/09/2018
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2093745e-86c0-4276-a7cc-a0187391ca4a
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04bb48f54347eabeb886d91fa245bae18c34de55
ms.sourcegitcommit: 50798e04fdcaf5dce5288aa18608e2a981b162fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2018
ms.locfileid: "29139294"
---
# <a name="wcf-adapters-property-schema-and-properties"></a><span data-ttu-id="68a00-102">WCF 配接器屬性結構描述和屬性</span><span class="sxs-lookup"><span data-stu-id="68a00-102">WCF Adapters Property Schema and Properties</span></span>
<span data-ttu-id="68a00-103">閱讀有關 WCF 配接器屬性結構描述中的升級屬性。</span><span class="sxs-lookup"><span data-stu-id="68a00-103">Read about the promoted properties in the WCF adapter property schema.</span></span> <span data-ttu-id="68a00-104">WCF 配接器會為您可以在應用程式中使用的屬性指派值。</span><span class="sxs-lookup"><span data-stu-id="68a00-104">The WCF adapters assign values to the properties that you can use in your application.</span></span> <span data-ttu-id="68a00-105">WCF 配接器也提供了一種將自訂屬性寫入但不升級至 BizTalk 訊息內容的機制，以及一種將自訂屬性升級至 BizTalk 訊息內容的機制。</span><span class="sxs-lookup"><span data-stu-id="68a00-105">WCF adapter also provides a mechanism to write but not promote the custom properties to the BizTalk message context, and a mechanism to promote the custom properties to the BizTalk message context.</span></span> <span data-ttu-id="68a00-106">如需詳細資訊，請參閱[SOAP 標頭與已發佈 WCF 服務](../core/soap-headers-with-published-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="68a00-106">For more details, see [SOAP Headers with Published WCF Services](../core/soap-headers-with-published-wcf-services.md).</span></span>  

## <a name="promoted-properties"></a><span data-ttu-id="68a00-107">升級屬性</span><span class="sxs-lookup"><span data-stu-id="68a00-107">Promoted properties</span></span>  
<span data-ttu-id="68a00-108">**命名空間︰** http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties</span><span class="sxs-lookup"><span data-stu-id="68a00-108">**Namespace:** http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties</span></span>  

#### <a name="action"></a><span data-ttu-id="68a00-109">動作</span><span class="sxs-lookup"><span data-stu-id="68a00-109">Action</span></span>
<span data-ttu-id="68a00-110">指定 **SOAPAction** 外寄訊息的標頭欄位。</span><span class="sxs-lookup"><span data-stu-id="68a00-110">Specify the **SOAPAction** header field for outgoing messages.</span></span> <span data-ttu-id="68a00-111">您可以將這個值指定兩個不同的方式︰ 單一動作格式和動作對應格式。</span><span class="sxs-lookup"><span data-stu-id="68a00-111">You can specify this value in two different ways: the single action format and the action mapping format.</span></span> <span data-ttu-id="68a00-112">如果您在單一動作格式中設定這個屬性 — 例如，http://contoso.com/Svc/Op1 — **SOAPAction**標頭外寄訊息一定會設定這個屬性中指定的值。</span><span class="sxs-lookup"><span data-stu-id="68a00-112">If you set this property in the single action format—for example, http://contoso.com/Svc/Op1 — the **SOAPAction** header for outgoing messages is always set to the value specified in this property.</span></span>

<span data-ttu-id="68a00-113">如果您設定此屬性以動作對應格式傳出 **SOAPAction** 標頭由 **BTS。作業** 內容屬性。</span><span class="sxs-lookup"><span data-stu-id="68a00-113">If you set this property in the action mapping format, the outgoing **SOAPAction** header is determined by the **BTS.Operation** context property.</span></span> <span data-ttu-id="68a00-114">例如，如果此屬性設定為下列 XML 格式和**BTS。作業**屬性設定為 Op1，WCF 傳送配接器會使用`http://contoso.com/Svc/Op1`針對外寄**SOAPAction**標頭。</span><span class="sxs-lookup"><span data-stu-id="68a00-114">For example, if this property is set to the following XML format and the **BTS.Operation** property is set to Op1, the WCF send adapter uses `http://contoso.com/Svc/Op1` for the outgoing **SOAPAction** header.</span></span>

```
<BtsActionMapping>
<Operation Name="Op1" Action="http://contoso.com/Svc/Op1">
<Operation Name="Op2" Action="http://contoso.com/Svc/Op2">
</BtsActionMapping>
```

<span data-ttu-id="68a00-115">協調流程執行個體如果外寄訊息是來自協調流程連接埠，以動態方式設定 **BTS。作業** 與連接埠的作業名稱的屬性。</span><span class="sxs-lookup"><span data-stu-id="68a00-115">If outgoing messages come from an orchestration port, orchestration instances dynamically set the **BTS.Operation** property with the operation name of the port.</span></span> <span data-ttu-id="68a00-116">如果外寄訊息會路由傳送，以內容為基礎的路由，您可以設定 **BTS。作業** 管線元件中的屬性。</span><span class="sxs-lookup"><span data-stu-id="68a00-116">If outgoing messages are routed with content-based routing, you can set the **BTS.Operation** property in pipeline components.</span></span>
<span data-ttu-id="68a00-117">這個屬性會以單一動作格式自動從內送訊息升級。</span><span class="sxs-lookup"><span data-stu-id="68a00-117">This property is automatically promoted from incoming messages with the single action format.</span></span>

<span data-ttu-id="68a00-118">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-118">Type: String</span></span>  
<span data-ttu-id="68a00-119">預設值： 空字串</span><span class="sxs-lookup"><span data-stu-id="68a00-119">Default value: An empty string</span></span>  
<span data-ttu-id="68a00-120">適用於： 所有 WCF 都傳送配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-120">Applies to: All WCF send adapters</span></span>

#### <a name="affiliateapplicationname"></a><span data-ttu-id="68a00-121">AffiliateApplicationName</span><span class="sxs-lookup"><span data-stu-id="68a00-121">AffiliateApplicationName</span></span>
<span data-ttu-id="68a00-122">指定要針對企業單一登入 (SSO) 使用的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="68a00-122">Specify the affiliate application to use for Enterprise Single Sign-On (SSO).</span></span> <span data-ttu-id="68a00-123">如果這個屬性，則需要 **UseSSO** 屬性設定為 **True**。</span><span class="sxs-lookup"><span data-stu-id="68a00-123">This property is required if the **UseSSO** property is set to **True**.</span></span> 

<span data-ttu-id="68a00-124">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-124">Type: String</span></span>  
<span data-ttu-id="68a00-125">預設值： 空字串</span><span class="sxs-lookup"><span data-stu-id="68a00-125">Default value: An empty string</span></span>  
<span data-ttu-id="68a00-126">適用於： 所有 WCF 都傳送配接器*除了*Wcf-netnamedpipe 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-126">Applies to: All WCF send adapters *except* the WCF-NetNamedPipe adapter</span></span>

#### <a name="algorithmsuite"></a><span data-ttu-id="68a00-127">AlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="68a00-127">AlgorithmSuite</span></span>
<span data-ttu-id="68a00-128">指定訊息加密和 Key Wrap 演算法。</span><span class="sxs-lookup"><span data-stu-id="68a00-128">Specify the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="68a00-129">這些演算法會對應到安全性原則語言 (WS-SecurityPolicy) 規格中所指定的演算法。</span><span class="sxs-lookup"><span data-stu-id="68a00-129">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>

<span data-ttu-id="68a00-130">如需有關適用值**AlgorithmSuite**屬性，請參閱**演算法套件**屬性**Wcf-nettcp 傳輸屬性對話方塊、 傳送、安全性** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="68a00-130">For more information about the applicable values for the **AlgorithmSuite** property, see the **Algorithm suite** property in the **WCF-NetTcp Transport Properties Dialog Box, Send, Security** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>

<span data-ttu-id="68a00-131">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-131">Type: String</span></span>  
<span data-ttu-id="68a00-132">預設值︰ **Basic256**</span><span class="sxs-lookup"><span data-stu-id="68a00-132">Default value: **Basic256**</span></span>  
<span data-ttu-id="68a00-133">適用於：</span><span class="sxs-lookup"><span data-stu-id="68a00-133">Applies to:</span></span> 

- <span data-ttu-id="68a00-134">WCF-BasicHttp 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-134">WCF-BasicHttp adapter</span></span>
- <span data-ttu-id="68a00-135">WCF-NetMsmq 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-135">WCF-NetMsmq adapter</span></span>
- <span data-ttu-id="68a00-136">WCF-NetTcp 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-136">WCF-NetTcp adapter</span></span>
- <span data-ttu-id="68a00-137">WCF-WSHttp 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-137">WCF-WSHttp adapter</span></span>

#### <a name="bindingconfiguration"></a><span data-ttu-id="68a00-138">BindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="68a00-138">BindingConfiguration</span></span>
<span data-ttu-id="68a00-139">指定的 XML 字串**\<繫結\>** 項目來設定不同類型的預先定義 Windows Communication Foundation (WCF) 所提供的繫結。</span><span class="sxs-lookup"><span data-stu-id="68a00-139">Specify an XML string with the **\<binding\>** element to configure different types of predefined bindings provided by Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="68a00-140">如需有關系統提供之繫結與自訂繫結的詳細資訊，請參考「請參閱」一節中的適當主題。</span><span class="sxs-lookup"><span data-stu-id="68a00-140">For more information about the system-provided binding and custom binding, see the appropriate topics in See Also.</span></span>

<span data-ttu-id="68a00-141">範例：</span><span class="sxs-lookup"><span data-stu-id="68a00-141">Example:</span></span>

```
<binding name="wsHttpBinding" transactionFlow="true">
<security><message clientCredentialType="UserName"></security>
</binding>
```

<span data-ttu-id="68a00-142">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-142">Type: String</span></span>  
<span data-ttu-id="68a00-143">預設值： 空字串</span><span class="sxs-lookup"><span data-stu-id="68a00-143">Default value: An empty string</span></span>  
<span data-ttu-id="68a00-144">適用於： Wcf-custom 配接器，Wcf-customisolated 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-144">Applies to: WCF-Custom adapter, WCF-CustomIsolated adapter</span></span>

#### <a name="bindingtype"></a><span data-ttu-id="68a00-145">BindingType</span><span class="sxs-lookup"><span data-stu-id="68a00-145">BindingType</span></span>
<span data-ttu-id="68a00-146">指定要用於端點的繫結類型。</span><span class="sxs-lookup"><span data-stu-id="68a00-146">Specify the type of the binding to use for the endpoint.</span></span> <span data-ttu-id="68a00-147">如需有關適用值**BindingType**屬性，請參閱**繫結的型別**屬性**Wcf-custom 傳輸屬性對話方塊、 傳送、 繫結**  索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="68a00-147">For more information about the applicable values for the **BindingType** property, see the **Binding Type** property in the **WCF-Custom Transport Properties Dialog Box, Send, Binding** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>

<span data-ttu-id="68a00-148">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-148">Type: String</span></span>  
<span data-ttu-id="68a00-149">預設值： 空字串</span><span class="sxs-lookup"><span data-stu-id="68a00-149">Default value: An empty string</span></span>  
<span data-ttu-id="68a00-150">適用於： Wcf-custom 配接器，Wcf-customisolated 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-150">Applies to: WCF-Custom adapter, WCF-CustomIsolated adapter</span></span>

#### <a name="clientcertificate"></a><span data-ttu-id="68a00-151">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="68a00-151">ClientCertificate</span></span>
<span data-ttu-id="68a00-152">指定 X.509 憑證的憑證指紋，以便向服務驗證此傳送埠。</span><span class="sxs-lookup"><span data-stu-id="68a00-152">Specify the thumbprint of the X.509 certificate for authenticating this send port to services.</span></span> <span data-ttu-id="68a00-153">如果這個屬性，則需要 **ClientCredentialsType** 屬性設定為 **憑證**。</span><span class="sxs-lookup"><span data-stu-id="68a00-153">This property is required if the **ClientCredentialsType** property is set to **Certificate**.</span></span> <span data-ttu-id="68a00-154">要用於此屬性的憑證必須安裝到 **我** 存放 **目前使用者** 位置。</span><span class="sxs-lookup"><span data-stu-id="68a00-154">The certificate to be used for this property must be installed into the **My** store in the **Current User** location.</span></span>

<span data-ttu-id="68a00-155">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-155">Type: String</span></span>  
<span data-ttu-id="68a00-156">預設值： 空字串</span><span class="sxs-lookup"><span data-stu-id="68a00-156">Default value: An empty string</span></span>  
<span data-ttu-id="68a00-157">適用於：</span><span class="sxs-lookup"><span data-stu-id="68a00-157">Applies to:</span></span> 

- <span data-ttu-id="68a00-158">WCF-BasicHttp 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-158">WCF-BasicHttp send adapter</span></span>
- <span data-ttu-id="68a00-159">WCF-WSHttp 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-159">WCF-WSHttp send adapter</span></span>
- <span data-ttu-id="68a00-160">WCF-NetTcp 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-160">WCF-NetTcp send adapter</span></span>
- <span data-ttu-id="68a00-161">WCF-NetMsmq 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-161">WCF-NetMsmq send adapter</span></span>

#### <a name="closetimeout"></a><span data-ttu-id="68a00-162">CloseTimeout</span><span class="sxs-lookup"><span data-stu-id="68a00-162">CloseTimeout</span></span>
<span data-ttu-id="68a00-163">指定時間值，表示可供完成通道關閉作業的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="68a00-163">Specify a time span value that indicates the interval of time provided for a channel close operation to complete.</span></span>

<span data-ttu-id="68a00-164">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-164">Type: String</span></span>  
<span data-ttu-id="68a00-165">預設值：00:01:00</span><span class="sxs-lookup"><span data-stu-id="68a00-165">Default value: 00:01:00</span></span>  
<span data-ttu-id="68a00-166">適用於： 所有 WCF 配接器*除了*Wcf-custom 和 Wcf-customisolated</span><span class="sxs-lookup"><span data-stu-id="68a00-166">Applies to: All WCF adapters *except* WCF-Custom and WCF-CustomIsolated</span></span>

#### <a name="customdeadletterqueue"></a><span data-ttu-id="68a00-167">CustomDeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="68a00-167">CustomDeadLetterQueue</span></span>
<span data-ttu-id="68a00-168">指定完整格式的 URI，連同 **net.msmq** 配置位置的每個應用程式寄不出信件佇列，已過期、 無法傳輸或傳遞的郵件放置的位置。</span><span class="sxs-lookup"><span data-stu-id="68a00-168">Specify the fully qualified URI with the **net.msmq** scheme for the location of the per-application dead-letter queue, where messages that have expired or that have failed transfer or delivery are placed.</span></span> <span data-ttu-id="68a00-169">例如，net.msmq://localhost/deadLetterQueueName。</span><span class="sxs-lookup"><span data-stu-id="68a00-169">For example, net.msmq://localhost/deadLetterQueueName.</span></span> <span data-ttu-id="68a00-170">無法寄出的信件佇列是傳送端應用程式之佇列管理員上的佇列，適用於傳遞失敗的過期訊息。</span><span class="sxs-lookup"><span data-stu-id="68a00-170">The dead-letter queue is a queue on the queue manager of the sending application for expired messages that have failed to be delivered.</span></span> <span data-ttu-id="68a00-171">如果這個屬性，則需要 **DeadLetterQueue** 屬性設定為 **自訂**。</span><span class="sxs-lookup"><span data-stu-id="68a00-171">This property is required if the **DeadLetterQueue** property is set to **Custom**.</span></span>

<span data-ttu-id="68a00-172">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-172">Type: String</span></span>  
<span data-ttu-id="68a00-173">預設值： 空字串</span><span class="sxs-lookup"><span data-stu-id="68a00-173">Default value: An empty string</span></span>  
<span data-ttu-id="68a00-174">適用於： Wcf-netmsmq 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-174">Applies to: WCF-NetMsmq send adapter</span></span>

#### <a name="deadletterqueue"></a><span data-ttu-id="68a00-175">DeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="68a00-175">DeadLetterQueue</span></span>
<span data-ttu-id="68a00-176">指定無法傳遞到應用程式的訊息將會傳輸到的無效信件佇列。</span><span class="sxs-lookup"><span data-stu-id="68a00-176">Specify the dead-letter queue where messages that have failed to be delivered to the application will be transferred.</span></span> <span data-ttu-id="68a00-177">如需有關訊息傳遞至寄不出信件佇列的詳細資訊，請參閱**Wcf-netmsmq 傳輸屬性對話方塊、 傳送、 繫結** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="68a00-177">For more information about the messages delivered to the dead-letter queue, see the **WCF-NetMsmq Transport Properties Dialog Box, Send, Binding** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>

<span data-ttu-id="68a00-178">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-178">Type: String</span></span>  
<span data-ttu-id="68a00-179">預設值︰ **系統**</span><span class="sxs-lookup"><span data-stu-id="68a00-179">Default value: **System**</span></span>  
<span data-ttu-id="68a00-180">適用於： Wcf-netmsmq 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-180">Applies to: WCF-NetMsmq send adapter</span></span>

#### <a name="disablelocationonfailure"></a><span data-ttu-id="68a00-181">DisableLocationOnFailure</span><span class="sxs-lookup"><span data-stu-id="68a00-181">DisableLocationOnFailure</span></span>
<span data-ttu-id="68a00-182">指定是否停用由於接收管線失敗或路由失敗造成輸入處理失敗的接收位置。</span><span class="sxs-lookup"><span data-stu-id="68a00-182">Specify whether to disable the receive location that fails inbound processing due to a receive pipeline failure or a routing failure.</span></span> <span data-ttu-id="68a00-183">您可能想要將此屬性設定為 **True** 當接收位置可以停用和拒絕服務 (DoS) 不是問題。</span><span class="sxs-lookup"><span data-stu-id="68a00-183">You may want to set this property to **True** when receive locations can be disabled and Denial-of-Service (DoS) is not a concern.</span></span>

<span data-ttu-id="68a00-184">例如：</span><span class="sxs-lookup"><span data-stu-id="68a00-184">For example:</span></span>  
- <span data-ttu-id="68a00-185">Wcf-custom 配接器： 當**BindingType**屬性設定為**netMsmqBinding**。</span><span class="sxs-lookup"><span data-stu-id="68a00-185">WCF-Custom adapter: When the **BindingType** property is set to **netMsmqBinding**.</span></span>
- <span data-ttu-id="68a00-186">Wcf-custom 配接器： 當**BindingType**屬性設定為**customBinding**，而**BindingConfiguration**屬性設定為使用依賴的自訂通道在已佇列之 MSMQ 等傳輸。</span><span class="sxs-lookup"><span data-stu-id="68a00-186">WCF-Custom adapter: When the **BindingType** property is set to **customBinding**, and the **BindingConfiguration** property is configured to use custom channels that rely on queued transports such as MSMQ.</span></span>
- <span data-ttu-id="68a00-187">Wcf-customisolated 配接器： 當**BindingType**屬性設定為**customBinding**，而**BindingConfiguration**屬性設定為使用自訂的通道依賴例如 MSMQ 佇列傳輸</span><span class="sxs-lookup"><span data-stu-id="68a00-187">WCF-CustomIsolated adapter: When the **BindingType** property is set to **customBinding**, and the **BindingConfiguration** property is configured to use custom channels that rely on queued transports such as MSMQ</span></span>
- <span data-ttu-id="68a00-188">WCF-NetMsmq 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-188">WCF-NetMsmq adapter</span></span>

<span data-ttu-id="68a00-189">類型：Boolean</span><span class="sxs-lookup"><span data-stu-id="68a00-189">Type: Boolean</span></span>  
<span data-ttu-id="68a00-190">預設值︰ **False**</span><span class="sxs-lookup"><span data-stu-id="68a00-190">Default: **False**</span></span>  
<span data-ttu-id="68a00-191">適用於：</span><span class="sxs-lookup"><span data-stu-id="68a00-191">Applies to:</span></span>  
- <span data-ttu-id="68a00-192">WCF-NetMsmq 接收配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-192">WCF-NetMsmq receive adapter</span></span>
- <span data-ttu-id="68a00-193">WCF-Custom 接收配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-193">WCF-Custom receive adapter</span></span>
- <span data-ttu-id="68a00-194">WCF-CustomIsolated 接收配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-194">WCF-CustomIsolated receive adapter</span></span>

#### <a name="enabletransaction"></a><span data-ttu-id="68a00-195">EnableTransaction</span><span class="sxs-lookup"><span data-stu-id="68a00-195">EnableTransaction</span></span>
<span data-ttu-id="68a00-196">這個屬性的效果會隨著 WCF 配接器而改變。</span><span class="sxs-lookup"><span data-stu-id="68a00-196">The effect of this property varies depending on the WCF adapter.</span></span> <span data-ttu-id="68a00-197">如需此屬性的詳細資訊，請參閱 < how to 主題中的每個 WCF 配接器[WCF 配接器](../core/wcf-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="68a00-197">For more information about this property, see how-to topics for each WCF adapter in [WCF Adapters](../core/wcf-adapters.md).</span></span>

<span data-ttu-id="68a00-198">類型：Boolean</span><span class="sxs-lookup"><span data-stu-id="68a00-198">Type: Boolean</span></span>  
<span data-ttu-id="68a00-199">適用於：</span><span class="sxs-lookup"><span data-stu-id="68a00-199">Applies to:</span></span> 

- <span data-ttu-id="68a00-200">WCF-WSHttp 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-200">WCF-WSHttp adapter</span></span>
- <span data-ttu-id="68a00-201">WCF-NetTcp 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-201">WCF-NetTcp adapter</span></span>
- <span data-ttu-id="68a00-202">WCF-NetNamedPipe 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-202">WCF-NetNamedPipe adapter</span></span>
- <span data-ttu-id="68a00-203">WCF-NetMsmq 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-203">WCF-NetMsmq adapter</span></span>

#### <a name="endpointbehaviorconfiguration"></a><span data-ttu-id="68a00-204">EndpointBehaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="68a00-204">EndpointBehaviorConfiguration</span></span>
<span data-ttu-id="68a00-205">指定的 XML 字串**\<行為\>** 元素**\<endpointBehaviors\>** 項目來設定的行為設定WCF 端點。</span><span class="sxs-lookup"><span data-stu-id="68a00-205">Specify an XML string with the **\<behavior\>** element of the **\<endpointBehaviors\>** element to configure the behavior settings of a WCF endpoint.</span></span> <span data-ttu-id="68a00-206">如需有關**\<endpointBehaviors\>** 項目，請參閱 < 另請參閱中的適當主題。</span><span class="sxs-lookup"><span data-stu-id="68a00-206">For more information about the **\<endpointBehaviors\>** element, see the appropriate topic in See Also.</span></span>

<span data-ttu-id="68a00-207">範例：</span><span class="sxs-lookup"><span data-stu-id="68a00-207">Example:</span></span> 
```
<behavior name="sampleBehavior"><callbackTimeouts/></behavior>
```

<span data-ttu-id="68a00-208">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-208">Type: String</span></span>  
<span data-ttu-id="68a00-209">預設值： 空字串</span><span class="sxs-lookup"><span data-stu-id="68a00-209">Default value: An empty string</span></span>  
<span data-ttu-id="68a00-210">適用於： Wcf-custom 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-210">Applies to: WCF-Custom send adapter</span></span>

#### <a name="establishsecuritycontext"></a><span data-ttu-id="68a00-211">EstablishSecurityContext</span><span class="sxs-lookup"><span data-stu-id="68a00-211">EstablishSecurityContext</span></span>
<span data-ttu-id="68a00-212">指定此安全性通道是否會建立安全的工作階段。</span><span class="sxs-lookup"><span data-stu-id="68a00-212">Specify whether the security channel establishes a secure session.</span></span> <span data-ttu-id="68a00-213">安全的工作階段會在交換應用程式訊息之前，先建立安全性內容語彙基元 (SCT)。</span><span class="sxs-lookup"><span data-stu-id="68a00-213">A secure session establishes a Security Context Token (SCT) before exchanging the application messages.</span></span>

<span data-ttu-id="68a00-214">類型：Boolean</span><span class="sxs-lookup"><span data-stu-id="68a00-214">Type: Boolean</span></span>  
<span data-ttu-id="68a00-215">預設值：True</span><span class="sxs-lookup"><span data-stu-id="68a00-215">Default value: True</span></span>  
<span data-ttu-id="68a00-216">套用至： Wcf-wshttp 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-216">Applied to: WCF-WSHttp adapter</span></span>

#### <a name="fromaddress"></a><span data-ttu-id="68a00-217">FromAddress</span><span class="sxs-lookup"><span data-stu-id="68a00-217">FromAddress</span></span>
<span data-ttu-id="68a00-218">指定用來傳送內送 WCF 訊息的來源端點位址。</span><span class="sxs-lookup"><span data-stu-id="68a00-218">Indicate the source endpoint address through which the incoming WCF messages are sent.</span></span> <span data-ttu-id="68a00-219">此屬性會自動從內送訊息升級。</span><span class="sxs-lookup"><span data-stu-id="68a00-219">The property is automatically promoted from incoming messages.</span></span>

<span data-ttu-id="68a00-220">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-220">Type: String</span></span>  
<span data-ttu-id="68a00-221">適用於： 所有 WCF 配接器*除了*Wcf-netmsmq 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-221">Applies to: All WCF adapters *except* the WCF-NetMsmq send adapter</span></span>
  
#### <a name="headers"></a><span data-ttu-id="68a00-222">標頭</span><span class="sxs-lookup"><span data-stu-id="68a00-222">Headers</span></span>
<span data-ttu-id="68a00-223">指定用來提供 URI 之外其他定址資訊的端點參考。</span><span class="sxs-lookup"><span data-stu-id="68a00-223">Specify the endpoint references used to provide additional addressing information beyond the URI.</span></span> <span data-ttu-id="68a00-224">使用這個屬性時，這個屬性必須具有\<**標頭**\>元素是根項目。</span><span class="sxs-lookup"><span data-stu-id="68a00-224">When this property is used, this property must have the \<**headers**\> element as the root element.</span></span> <span data-ttu-id="68a00-225">所有位址標頭必須置於\<**標頭**\>項目。</span><span class="sxs-lookup"><span data-stu-id="68a00-225">All of the address headers must be placed inside the \<**headers**\> element.</span></span> <span data-ttu-id="68a00-226">內送訊息的這個屬性會自動升級。</span><span class="sxs-lookup"><span data-stu-id="68a00-226">This property is automatically promoted for incoming messages.</span></span>

<span data-ttu-id="68a00-227">範例：</span><span class="sxs-lookup"><span data-stu-id="68a00-227">Example:</span></span>
```
<headers>
<Region xmlns="Uri">"String"</Region>
<Member xmlns="Uri">"String"</Member> 
</headers>
```

<span data-ttu-id="68a00-228">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-228">Type: String</span></span>  
<span data-ttu-id="68a00-229">適用於： 所有 WCF 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-229">Applies to: All WCF adapters</span></span>
  
#### <a name="identity"></a><span data-ttu-id="68a00-230">識別</span><span class="sxs-lookup"><span data-stu-id="68a00-230">Identity</span></span>
<span data-ttu-id="68a00-231">指定接收位置或傳送埠所預期之服務的識別。</span><span class="sxs-lookup"><span data-stu-id="68a00-231">Specify the identity of the service that a receive location provides or a send port expects.</span></span> <span data-ttu-id="68a00-232">您可以指定的值 **識別** 屬性，則根據安全性組態而有所不同。</span><span class="sxs-lookup"><span data-stu-id="68a00-232">The values that can be specified for the **Identity** property differ according to the security configuration.</span></span> <span data-ttu-id="68a00-233">這些設定可讓用戶端驗證服務。</span><span class="sxs-lookup"><span data-stu-id="68a00-233">These settings enable clients to authenticate services.</span></span> <span data-ttu-id="68a00-234">在用戶端與服務之間的交握程序中，Windows Communication Foundation (WCF) 基礎結構可確保服務的識別能夠與用戶端的值相符。</span><span class="sxs-lookup"><span data-stu-id="68a00-234">In the handshake process between clients and services, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the services matches the values of the clients.</span></span>

<span data-ttu-id="68a00-235">範例：</span><span class="sxs-lookup"><span data-stu-id="68a00-235">Example:</span></span>
```
<identity>
<userPrincipalName value="username@contoso.com"/>
</identity>
```

<span data-ttu-id="68a00-236">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-236">Type: String</span></span>  
<span data-ttu-id="68a00-237">預設值： 空字串</span><span class="sxs-lookup"><span data-stu-id="68a00-237">Default value: An empty string</span></span>  
<span data-ttu-id="68a00-238">適用於： 所有 WCF 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-238">Applies to: All WCF adapters</span></span>

#### <a name="inboundbodylocation"></a><span data-ttu-id="68a00-239">InboundBodyLocation</span><span class="sxs-lookup"><span data-stu-id="68a00-239">InboundBodyLocation</span></span>
<span data-ttu-id="68a00-240">指定資料選取範圍 soap **主體** 內送 WCF 訊息的項目。</span><span class="sxs-lookup"><span data-stu-id="68a00-240">Specify the data selection for the SOAP **Body** element of incoming WCF messages.</span></span> <span data-ttu-id="68a00-241">如需有關如何使用**InboundBodyLocation**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="68a00-241">For more information about how to use the **InboundBodyLocation** property, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md).</span></span>

<span data-ttu-id="68a00-242">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-242">Type: String</span></span>  
<span data-ttu-id="68a00-243">預設值： UseBodyElement</span><span class="sxs-lookup"><span data-stu-id="68a00-243">Default value: UseBodyElement</span></span>  

    Applicable values are:  
        - UseBodyElement: Use the content of the SOAP **Body** element of an incoming message to create the BizTalk message body part. If the **Body** element has more than one child element, only the first element becomes the BizTalk message body part.
        - UseEnvelope: Create the BizTalk message body part from the entire SOAP **Envelope** of an incoming message.
        - UseBodyPath: Use the body path expression in the **InboundBodyPathExpression** property to create the BizTalk message body part. The body path expression is evaluated against the immediate child element of the SOAP **Body** element of an incoming message. This property is valid only for solicit-response ports.  

<span data-ttu-id="68a00-244">適用於： 所有 WCF 配接器*除了*Wcf-netmsmq 傳送</span><span class="sxs-lookup"><span data-stu-id="68a00-244">Applies to: All WCF adapters *except* WCF-NetMsmq send</span></span>  

#### <a name="inboundbodypathexpression"></a><span data-ttu-id="68a00-245">InboundBodyPathExpression</span><span class="sxs-lookup"><span data-stu-id="68a00-245">InboundBodyPathExpression</span></span>
<span data-ttu-id="68a00-246">指定內文路徑運算式來識別用於建立 BizTalk 訊息內文部分之內送訊息的特定部分。</span><span class="sxs-lookup"><span data-stu-id="68a00-246">Specify the body path expression to identify a specific part of an incoming message used to create the BizTalk message body part.</span></span> <span data-ttu-id="68a00-247">此內文路徑運算式評估的 soap 的直系子項目 **主體** 內送訊息的節點。</span><span class="sxs-lookup"><span data-stu-id="68a00-247">This body path expression is evaluated against the immediate child element of the SOAP **Body** node of an incoming message.</span></span> <span data-ttu-id="68a00-248">如果此內文路徑運算式傳回一個以上的節點，則只會為 BizTalk 訊息內文部分選擇第一個節點。</span><span class="sxs-lookup"><span data-stu-id="68a00-248">If this body path expression returns more than one node, only the first node is chosen for the BizTalk message body part.</span></span> <span data-ttu-id="68a00-249">如果這個屬性，則需要 **InboundBodyLocation** 屬性設定為 **UseBodyPath**。</span><span class="sxs-lookup"><span data-stu-id="68a00-249">This property is required if the **InboundBodyLocation** property is set to **UseBodyPath**.</span></span> <span data-ttu-id="68a00-250">如需有關如何使用**InboundBodyPathExpression**屬性，請參閱[WCF 配接器屬性結構描述和屬性](../core/wcf-adapters-property-schema-and-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="68a00-250">For more information about how to use the **InboundBodyPathExpression** property, see [WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md).</span></span>

<span data-ttu-id="68a00-251">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-251">Type: String</span></span>  
<span data-ttu-id="68a00-252">預設值： 空字串</span><span class="sxs-lookup"><span data-stu-id="68a00-252">Default value: An empty string</span></span>  
<span data-ttu-id="68a00-253">適用於： 所有 WCF 配接器*除了*Wcf-netmsmq 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-253">Applies to: All WCF adapters *except* the WCF-NetMsmq send adapter</span></span>

#### <a name="inboundheaders"></a><span data-ttu-id="68a00-254">InboundHeaders</span><span class="sxs-lookup"><span data-stu-id="68a00-254">InboundHeaders</span></span>
<span data-ttu-id="68a00-255">使用 **InboundHeaders** 屬性來存取內送 WCF 訊息的 SOAP 標頭。</span><span class="sxs-lookup"><span data-stu-id="68a00-255">Use the **InboundHeaders** property to access the SOAP headers of incoming WCF messages.</span></span> <span data-ttu-id="68a00-256">WCF 配接器會將內送訊息中的所有 SOAP 標頭值複製到這個屬性，包括 WCF 基礎結構用於WS-Addressing、WS-Security 和 WS-AtomicTransaction 等的自訂 SOAP 標頭和標準 SOAP 標頭。</span><span class="sxs-lookup"><span data-stu-id="68a00-256">The WCF adapters copy all the SOAP header values in inbound messages to this property, which include custom SOAP headers and standard SOAP headers that the WCF infrastructure uses for such as WS-Addressing, WS-Security, and WS-AtomicTransaction.</span></span> <span data-ttu-id="68a00-257">內容屬性中所包含的值是包含 XML 資料字串\<**標頭**\>根項目，並傳入的 SOAP 標頭複製成為子項目的\< **標頭**\>項目。</span><span class="sxs-lookup"><span data-stu-id="68a00-257">The value contained in the context property is a string containing XML data with the \<**headers**\> root element, and the incoming SOAP headers are copied as child elements of the \<**headers**\> element.</span></span> <span data-ttu-id="68a00-258">使用 WCF 配接器如何存取 SOAP 標頭的相關資訊，請參閱 SDK 範例中，使用自訂 SOAP 標頭使用 WCF 配接器，從 [http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960)。</span><span class="sxs-lookup"><span data-stu-id="68a00-258">For more information about how to access SOAP headers with the WCF adapters, see the SDK sample, Using Custom SOAP Headers with the WCF Adapters, from [http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960).</span></span>

<span data-ttu-id="68a00-259">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-259">Type: String</span></span>  
<span data-ttu-id="68a00-260">適用於： 所有 WCF 配接器*除了*Wcf-netmsmq 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-260">Applies to: All WCF adapters *except* the WCF-NetMsmq send adapter</span></span>

#### <a name="inboundnodeencoding"></a><span data-ttu-id="68a00-261">InboundNodeEncoding</span><span class="sxs-lookup"><span data-stu-id="68a00-261">InboundNodeEncoding</span></span>
<span data-ttu-id="68a00-262">指定的編碼的 WCF 接收配接器，用來解碼中指定的內文路徑運算式所識別的節點類型 **InboundBodyPathExpression**。</span><span class="sxs-lookup"><span data-stu-id="68a00-262">Specify the type of encoding that the WCF receive adapter uses to decode the node identified by the body path expression specified in **InboundBodyPathExpression**.</span></span> <span data-ttu-id="68a00-263">如果這個屬性，則需要 **InboundBodyLocation** 屬性設定為 **UseBodyPath**。</span><span class="sxs-lookup"><span data-stu-id="68a00-263">This property is required if the **InboundBodyLocation** property is set to **UseBodyPath**.</span></span>

<span data-ttu-id="68a00-264">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-264">Type: String</span></span>  
<span data-ttu-id="68a00-265">預設值： XML</span><span class="sxs-lookup"><span data-stu-id="68a00-265">Default value: XML</span></span>  

    Applicable values are:  
        - Base64: Base64 encoding
        - Hex: Hexadecimal encoding
        - String: Text encoding - UTF-8
        - XML: The WCF adapters create the BizTalk message body with the outer XML of the node selected by the body path expression in **InboundBodyPathExpression**.  

<span data-ttu-id="68a00-266">適用於： 所有 WCF 配接器*除了*Wcf-netmsmq 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-266">Applies to: All WCF adapters *except* the WCF-NetMsmq send adapter</span></span>

#### <a name="isfault"></a><span data-ttu-id="68a00-267">IsFault</span><span class="sxs-lookup"><span data-stu-id="68a00-267">IsFault</span></span>
<span data-ttu-id="68a00-268">指出是否收到 SOAP 錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="68a00-268">Indicate whether SOAP fault messages are received.</span></span> <span data-ttu-id="68a00-269">此屬性會自動從內送訊息升級。</span><span class="sxs-lookup"><span data-stu-id="68a00-269">The property is automatically promoted from incoming messages.</span></span> 

<span data-ttu-id="68a00-270">**附註**</span><span class="sxs-lookup"><span data-stu-id="68a00-270">**Note**</span></span>  
<span data-ttu-id="68a00-271">**IsFault**屬性不能用來檢查所接收的訊息傳輸錯誤，例如 HTTP 404 （檔案或目錄找不到） 錯誤。</span><span class="sxs-lookup"><span data-stu-id="68a00-271">The **IsFault** property cannot be used to check the received messages for transport errors such as the HTTP 404 (File or Directory Not Found) error.</span></span>

<span data-ttu-id="68a00-272">類型：Boolean</span><span class="sxs-lookup"><span data-stu-id="68a00-272">Type: Boolean</span></span>  
<span data-ttu-id="68a00-273">適用於： 所有 WCF 配接器*除了*Wcf-netmsmq 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-273">Applies to: All WCF adapters *except* the WCF-NetMsmq send adapter</span></span>

#### <a name="leasetimeout"></a><span data-ttu-id="68a00-274">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="68a00-274">LeaseTimeout</span></span>
<span data-ttu-id="68a00-275">指定作用中之集區連線的最大存留期間。</span><span class="sxs-lookup"><span data-stu-id="68a00-275">Specify the maximum lifetime of an active pooled connection.</span></span> <span data-ttu-id="68a00-276">在指定的時間過去後，目前的要求獲得服務之後，連線隨即會關閉。</span><span class="sxs-lookup"><span data-stu-id="68a00-276">After the specified time elapses, the connection closes after the current request is serviced.</span></span>

<span data-ttu-id="68a00-277">Wcf-nettcp 配接器會利用 [NetTcpBinding](http://go.microsoft.com/fwlink/?LinkId=81087) 類別與端點進行通訊。</span><span class="sxs-lookup"><span data-stu-id="68a00-277">The WCF-NetTcp adapter leverages the [NetTcpBinding](http://go.microsoft.com/fwlink/?LinkId=81087) class to communicate with an endpoint.</span></span> <span data-ttu-id="68a00-278">當使用 [NetTcpBinding](http://go.microsoft.com/fwlink/?LinkId=81087) 在負載平衡案例中，請考慮減少預設租用逾時。如需詳細資訊時使用之負載平衡[NetTcpBinding](http://go.microsoft.com/fwlink/?LinkId=81087)，請參閱 < 另請參閱中的適當主題。</span><span class="sxs-lookup"><span data-stu-id="68a00-278">When using the [NetTcpBinding](http://go.microsoft.com/fwlink/?LinkId=81087) in load-balanced scenarios, consider reducing the default lease time-out. For more information about load balancing when using the [NetTcpBinding](http://go.microsoft.com/fwlink/?LinkId=81087), see the appropriate topic in See Also.</span></span>

<span data-ttu-id="68a00-279">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-279">Type: String</span></span>  
<span data-ttu-id="68a00-280">預設值︰ 00:05:00</span><span class="sxs-lookup"><span data-stu-id="68a00-280">Default value: 00:05:00</span></span>  
<span data-ttu-id="68a00-281">適用於： Wcf-nettcp 接收配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-281">Applies to: WCF-NetTcp receive adapter</span></span>  

#### <a name="maxconcurrentcalls"></a><span data-ttu-id="68a00-282">MaxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="68a00-282">MaxConcurrentCalls</span></span>
<span data-ttu-id="68a00-283">指定對單一服務執行個體的並行呼叫數目。</span><span class="sxs-lookup"><span data-stu-id="68a00-283">Specify the number of concurrent calls to a single service instance.</span></span> <span data-ttu-id="68a00-284">超出上限的呼叫將排入佇列。</span><span class="sxs-lookup"><span data-stu-id="68a00-284">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="68a00-285">將這個值設定為 0 的效果與設定為 **Int32.MaxValue**相同。</span><span class="sxs-lookup"><span data-stu-id="68a00-285">Setting this value to 0 is equivalent to setting it to **Int32.MaxValue**.</span></span> 

<span data-ttu-id="68a00-286">**附註**</span><span class="sxs-lookup"><span data-stu-id="68a00-286">**Note**</span></span>  
<span data-ttu-id="68a00-287">您無法使用追蹤設定檔在 BAM 主要匯入資料庫中追蹤這個屬性。</span><span class="sxs-lookup"><span data-stu-id="68a00-287">This property cannot be tracked in the BAM Primary Import database with tracking profiles.</span></span> 

<span data-ttu-id="68a00-288">類型： 整數</span><span class="sxs-lookup"><span data-stu-id="68a00-288">Type: Integer</span></span>  
<span data-ttu-id="68a00-289">預設值：200</span><span class="sxs-lookup"><span data-stu-id="68a00-289">Default value: 200</span></span>  
<span data-ttu-id="68a00-290">適用於： 所有 WCF 都接收配接器*除了*Wcf-custom 和 Wcf-customisolated 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-290">Applies to: All WCF receive adapters *except* the WCF-Custom and WCF-CustomIsolated adapters</span></span>

#### <a name="maxconnections"></a><span data-ttu-id="68a00-291">MaxConnections</span><span class="sxs-lookup"><span data-stu-id="68a00-291">MaxConnections</span></span>
<span data-ttu-id="68a00-292">指定待命程式最多可以擁有等待應用程式接受的連線數目。</span><span class="sxs-lookup"><span data-stu-id="68a00-292">Specify the maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="68a00-293">超過此配額值時，則會捨棄新的傳入連線，而非等待接受連線。</span><span class="sxs-lookup"><span data-stu-id="68a00-293">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span> 

<span data-ttu-id="68a00-294">**附註**</span><span class="sxs-lookup"><span data-stu-id="68a00-294">**Note**</span></span>  
<span data-ttu-id="68a00-295">因為這是配接器處理常式屬性，所以無法在管線元件和協調流程中設定。</span><span class="sxs-lookup"><span data-stu-id="68a00-295">Because this is an adapter handler property, this property cannot be configured in pipeline components and orchestrations.</span></span> 

<span data-ttu-id="68a00-296">**附註**</span><span class="sxs-lookup"><span data-stu-id="68a00-296">**Note**</span></span>  
<span data-ttu-id="68a00-297">您無法使用追蹤設定檔在 BAM 主要匯入資料庫中追蹤這個屬性。</span><span class="sxs-lookup"><span data-stu-id="68a00-297">This property cannot be tracked in the BAM Primary Import database with tracking profiles.</span></span> 

<span data-ttu-id="68a00-298">類型： 整數</span><span class="sxs-lookup"><span data-stu-id="68a00-298">Type: Integer</span></span>  
<span data-ttu-id="68a00-299">預設值︰ 10</span><span class="sxs-lookup"><span data-stu-id="68a00-299">Default value: 10</span></span>  
<span data-ttu-id="68a00-300">適用於： Wcf-netnamedpipe 配接器，Wcf-nettcp 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-300">Applies to: WCF-NetNamedPipe adapter, WCF-NetTcp adapter</span></span>  

#### <a name="maxreceivedmessagesize"></a><span data-ttu-id="68a00-301">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="68a00-301">MaxReceivedMessageSize</span></span>
<span data-ttu-id="68a00-302">指定大小上限，以位元組為單位，在網路上可以接收的訊息 （包括標頭）。</span><span class="sxs-lookup"><span data-stu-id="68a00-302">Specify the maximum size, in bytes, for a message (including headers) that can be received on the wire.</span></span> <span data-ttu-id="68a00-303">訊息的大小受限於配置給每個訊息的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="68a00-303">The size of the messages is bounded by the amount of memory allocated for each message.</span></span> <span data-ttu-id="68a00-304">您可以使用這個屬性來限制遭受拒絕服務 (DoS) 攻擊的風險程度。</span><span class="sxs-lookup"><span data-stu-id="68a00-304">You can use this property to limit exposure to denial of service (DoS) attacks.</span></span>

<span data-ttu-id="68a00-305">類型： 整數</span><span class="sxs-lookup"><span data-stu-id="68a00-305">Type: Integer</span></span>  
<span data-ttu-id="68a00-306">預設值：65536</span><span class="sxs-lookup"><span data-stu-id="68a00-306">Default value: 65536</span></span>  
<span data-ttu-id="68a00-307">適用於：</span><span class="sxs-lookup"><span data-stu-id="68a00-307">Applies to:</span></span> 
- <span data-ttu-id="68a00-308">WCF-BasicHttp 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-308">WCF-BasicHttp adapter</span></span>
- <span data-ttu-id="68a00-309">WCF-WSHttp 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-309">WCF-WSHttp adapter</span></span>
- <span data-ttu-id="68a00-310">WCF-NetTcp 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-310">WCF-NetTcp adapter</span></span>
- <span data-ttu-id="68a00-311">WCF-NetNamedPipe 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-311">WCF-NetNamedPipe adapter</span></span>
- <span data-ttu-id="68a00-312">WCF-NetMsmq 接收配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-312">WCF-NetMsmq receive adapter</span></span>

#### <a name="messageclientcredentialtype"></a><span data-ttu-id="68a00-313">MessageClientCredentialType</span><span class="sxs-lookup"><span data-stu-id="68a00-313">MessageClientCredentialType</span></span>
<span data-ttu-id="68a00-314">指定當使用以訊息為基礎的安全性來執行用戶端驗證時，所要使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="68a00-314">Specify the type of credential to be used when performing client authentication using message-based security.</span></span>

<span data-ttu-id="68a00-315">每個 WCF 配接器適用的值都不一樣。</span><span class="sxs-lookup"><span data-stu-id="68a00-315">The applicable values differ for each WCF adapter.</span></span> <span data-ttu-id="68a00-316">如需有關**MessageClientCredentialType**屬性，請參閱使用說明主題中的每個 WCF 配接器[WCF 配接器](../core/wcf-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="68a00-316">For more information about the **MessageClientCredentialType** property, see how-to topics for each WCF adapter in [WCF Adapters](../core/wcf-adapters.md).</span></span>

<span data-ttu-id="68a00-317">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-317">Type: String</span></span>  
<span data-ttu-id="68a00-318">適用於：</span><span class="sxs-lookup"><span data-stu-id="68a00-318">Applies to:</span></span> 
- <span data-ttu-id="68a00-319">WCF-BasicHttp 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-319">WCF-BasicHttp adapter</span></span>
- <span data-ttu-id="68a00-320">WCF-WSHttp 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-320">WCF-WSHttp adapter</span></span>
- <span data-ttu-id="68a00-321">WCF-NetTcp 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-321">WCF-NetTcp adapter</span></span>
- <span data-ttu-id="68a00-322">WCF-NetNamedPipe 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-322">WCF-NetNamedPipe adapter</span></span>

#### <a name="messageencoding"></a><span data-ttu-id="68a00-323">MessageEncoding</span><span class="sxs-lookup"><span data-stu-id="68a00-323">MessageEncoding</span></span>
<span data-ttu-id="68a00-324">指定用來為 SOAP 訊息編碼的編碼器。</span><span class="sxs-lookup"><span data-stu-id="68a00-324">Specify the encoder used to encode the SOAP message.</span></span>

<span data-ttu-id="68a00-325">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-325">Type: String</span></span>  
<span data-ttu-id="68a00-326">預設值︰ 文字</span><span class="sxs-lookup"><span data-stu-id="68a00-326">Default value: Text</span></span>  

    Applicable values: 
        - Text: Use a text message encoder
        - Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder  

<span data-ttu-id="68a00-327">適用於： Wcf-basichttp 配接器、 Wcf-wshttp 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-327">Applies to: WCF-BasicHttp adapter, WCF-WSHttp adapter</span></span>


#### <a name="msmqauthenticationmode"></a><span data-ttu-id="68a00-328">MsmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="68a00-328">MsmqAuthenticationMode</span></span>
<span data-ttu-id="68a00-329">指定訊息如何由 MSMQ 傳輸進行驗證。</span><span class="sxs-lookup"><span data-stu-id="68a00-329">Specify how the message must be authenticated by the MSMQ transport.</span></span>

<span data-ttu-id="68a00-330">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-330">Type: String</span></span>  
<span data-ttu-id="68a00-331">預設值︰ **WindowsDomain**</span><span class="sxs-lookup"><span data-stu-id="68a00-331">Default value: **WindowsDomain**</span></span>  
    <span data-ttu-id="68a00-332">如需有關適用值**MsmqAuthenticationMode**屬性，請參閱**MSMQ 驗證模式**屬性**Wcf-netmsmq 傳輸屬性對話方塊方塊中，傳送、 安全性** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="68a00-332">For more information about the applicable values for the **MsmqAuthenticationMode** property, see the **MSMQ authentication mode** property in the **WCF-NetMsmq Transport Properties Dialog Box, Send, Security** tab [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
<span data-ttu-id="68a00-333">適用於： Wcf-netmsmq 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-333">Applies to: WCF-NetMsmq adapter</span></span>  

#### <a name="msmqencryptionalgorithm"></a><span data-ttu-id="68a00-334">MsmqEncryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="68a00-334">MsmqEncryptionAlgorithm</span></span>
<span data-ttu-id="68a00-335">指定在訊息佇列管理員之間傳輸訊息時，要在連線上使用之訊息加密的演算法。</span><span class="sxs-lookup"><span data-stu-id="68a00-335">Specify the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="68a00-336">這個屬性只有當 **MsmqProtectionLevel** 屬性設定為 **EncryptAndSign**。</span><span class="sxs-lookup"><span data-stu-id="68a00-336">This property is available only if the **MsmqProtectionLevel** property is set to **EncryptAndSign**.</span></span>

<span data-ttu-id="68a00-337">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-337">Type: String</span></span>  
<span data-ttu-id="68a00-338">預設值︰ **RC4Stream**</span><span class="sxs-lookup"><span data-stu-id="68a00-338">Default value: **RC4Stream**</span></span>  

    Applicable values are: RC4Stream, AES

<span data-ttu-id="68a00-339">適用於： Wcf-netmsmq 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-339">Applies to: WCF-NetMsmq adapter</span></span>  

#### <a name="msmqprotectionlevel"></a><span data-ttu-id="68a00-340">MsmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="68a00-340">MsmqProtectionLevel</span></span>
<span data-ttu-id="68a00-341">指定在 MSMQ 傳輸層維持訊息安全的方式。</span><span class="sxs-lookup"><span data-stu-id="68a00-341">Specify the way messages are secured at the level of the MSMQ transport.</span></span>

<span data-ttu-id="68a00-342">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-342">Type: String</span></span>  
<span data-ttu-id="68a00-343">預設值︰ **符號**</span><span class="sxs-lookup"><span data-stu-id="68a00-343">Default value: **Sign**</span></span>  

    Applicable values are:
        - None: No protection
        - Sign: Messages are signed
        - EncryptAndSign: Messages are encrypted and signed. To use this protection level, you must enable **Active Directory Integration** for **MSMQ**  

<span data-ttu-id="68a00-344">適用於： Wcf-netmsmq 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-344">Applies to: WCF-NetMsmq adapter</span></span>  

#### <a name="msmqsecurehashalgorithm"></a><span data-ttu-id="68a00-345">MsmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="68a00-345">MsmqSecureHashAlgorithm</span></span>
<span data-ttu-id="68a00-346">指定用來計算雜湊的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="68a00-346">Specify the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="68a00-347">這個屬性不會使用如果 **MsmqProtectionLevel** 屬性設定為 **無**。</span><span class="sxs-lookup"><span data-stu-id="68a00-347">This property is not available if the **MsmqProtectionLevel** property is set to **None**.</span></span>

<span data-ttu-id="68a00-348">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-348">Type: String</span></span>  
<span data-ttu-id="68a00-349">預設值︰ **SHA1**</span><span class="sxs-lookup"><span data-stu-id="68a00-349">Default value: **SHA1**</span></span>  

    Applicable values are: MD5, SHA1, SHA25, SHA512  

<span data-ttu-id="68a00-350">適用於： Wcf-netmsmq 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-350">Applies to: WCF-NetMsmq adapter</span></span>  

#### <a name="negotiateservicecredential"></a><span data-ttu-id="68a00-351">NegotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="68a00-351">NegotiateServiceCredential</span></span>
<span data-ttu-id="68a00-352">指定是否會在超出範圍的用戶端提供此服務認證，或是透過交涉程序從此服務取得服務認證給用戶端。</span><span class="sxs-lookup"><span data-stu-id="68a00-352">Specify whether the service credential is provisioned at the client out of band, or is obtained from the service to the client through a process of negotiation.</span></span> <span data-ttu-id="68a00-353">這類交涉是一般訊息交換的先驅。</span><span class="sxs-lookup"><span data-stu-id="68a00-353">Such a negotiation is a precursor to the usual message exchange.</span></span>

<span data-ttu-id="68a00-354">如果 **MessageClientCredentialType** 屬性等於 **無**, ，**Username**, ，或 **憑證**, ，此屬性設定為 **False** 意指服務憑證可超出用戶端，且用戶端必須指定服務憑證。</span><span class="sxs-lookup"><span data-stu-id="68a00-354">If the **MessageClientCredentialType** property equals **None**, **Username**, or **Certificate**, setting this property to **False** implies that the service certificate is available at the client out of band and that the client needs to specify the service certificate.</span></span> <span data-ttu-id="68a00-355">這個模式可以與 SOAP 堆疊交互運作 (SOAP 堆疊會實作 WS-Trust 和 WS-SecureConversation)。</span><span class="sxs-lookup"><span data-stu-id="68a00-355">This mode is interoperable with SOAP stacks that implement WS-Trust and WS-SecureConversation.</span></span>

<span data-ttu-id="68a00-356">如果 **MessageClientCredentialType** 屬性設定為 **Windows**, ，此屬性設定為 **False** 指定 Kerberos 驗證。</span><span class="sxs-lookup"><span data-stu-id="68a00-356">If the **MessageClientCredentialType** property is set to **Windows**, setting this property to **False** specifies Kerberos-based authentication.</span></span> <span data-ttu-id="68a00-357">這表示，用戶端和服務都必須是相同 Kerberos 網域的一部分。</span><span class="sxs-lookup"><span data-stu-id="68a00-357">This means that the client and service must be part of the same Kerberos domain.</span></span> <span data-ttu-id="68a00-358">這個模式可以與 SOAP 堆疊交互運作，SOAP 堆疊會實作 Kerberos Token 設定檔 (如 OASIS WSS TC 上所定義) 以及 WS-Trust 和 WS-SecureConversation。</span><span class="sxs-lookup"><span data-stu-id="68a00-358">This mode is interoperable with SOAP stacks that implement the Kerberos token profile (as defined at OASIS WSS TC) as well as WS-Trust and WS-SecureConversation.</span></span>

<span data-ttu-id="68a00-359">當這個屬性是 **True**, ，會造成透過 SOAP 訊息傳送 SPNego 交換的.NET SOAP 交涉。</span><span class="sxs-lookup"><span data-stu-id="68a00-359">When this property is **True**, it causes a .NET SOAP negotiation that tunnels SPNego exchange over SOAP messages.</span></span>

<span data-ttu-id="68a00-360">類型：Boolean</span><span class="sxs-lookup"><span data-stu-id="68a00-360">Type: Boolean</span></span>  
<span data-ttu-id="68a00-361">預設值：True</span><span class="sxs-lookup"><span data-stu-id="68a00-361">Default value: True</span></span>  
<span data-ttu-id="68a00-362">適用於： Wcf-wshttp 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-362">Applies to: WCF-WSHttp adapter</span></span>  

#### <a name="opentimeout"></a><span data-ttu-id="68a00-363">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="68a00-363">OpenTimeout</span></span>
<span data-ttu-id="68a00-364">指定時間值，表示可供完成通道開啟作業的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="68a00-364">Specify a time span value that indicates the interval of time provided for a channel open operation to complete.</span></span> 

<span data-ttu-id="68a00-365">**附註**</span><span class="sxs-lookup"><span data-stu-id="68a00-365">**Note**</span></span>  
<span data-ttu-id="68a00-366">您無法使用追蹤設定檔在 BAM 主要匯入資料庫中追蹤這個屬性。</span><span class="sxs-lookup"><span data-stu-id="68a00-366">This property cannot be tracked in the BAM Primary Import database with tracking profiles.</span></span> 

<span data-ttu-id="68a00-367">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-367">Type: String</span></span>  
<span data-ttu-id="68a00-368">預設值：00:01:00</span><span class="sxs-lookup"><span data-stu-id="68a00-368">Default value: 00:01:00</span></span>  
<span data-ttu-id="68a00-369">適用於： 所有 WCF 配接器*除了*Wcf-custom 和 Wcf-customisolated 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-369">Applies to: All WCF adapters *except* the WCF-Custom and WCF-CustomIsolated adapters</span></span>

#### <a name="orderedprocessing"></a><span data-ttu-id="68a00-370">OrderedProcessing</span><span class="sxs-lookup"><span data-stu-id="68a00-370">OrderedProcessing</span></span>
<span data-ttu-id="68a00-371">指定是否連續處理訊息。</span><span class="sxs-lookup"><span data-stu-id="68a00-371">Specify whether to process messages serially.</span></span> <span data-ttu-id="68a00-372">選取此屬性時，此接收位置所能容納已排序的訊息傳遞的 BizTalk 傳訊 」 或 「 協調流程傳送埠搭配使用時 **排序的傳遞** 選項設為 `True`。</span><span class="sxs-lookup"><span data-stu-id="68a00-372">When this property is selected, this receive location accommodates ordered message delivery when used in conjunction with a BizTalk messaging or orchestration send port that has the **Ordered Delivery** option set to `True`.</span></span> <span data-ttu-id="68a00-373">如需詳細資訊 **排序的傳遞** 選項，請參閱 < 另請參閱中的適當主題。</span><span class="sxs-lookup"><span data-stu-id="68a00-373">For more information about the **Ordered Delivery** option, see the appropriate topics in See Also.</span></span>

<span data-ttu-id="68a00-374">這個屬性適用於下列情況：</span><span class="sxs-lookup"><span data-stu-id="68a00-374">This property is applicable in the following cases:</span></span>
- <span data-ttu-id="68a00-375">Wcf-custom 配接器： 當**BindingType**屬性設定為**netMsmqBinding**</span><span class="sxs-lookup"><span data-stu-id="68a00-375">WCF-Custom adapter: When the **BindingType** property is set to **netMsmqBinding**</span></span>
- <span data-ttu-id="68a00-376">Wcf-custom 配接器： 當**BindingType**屬性設定為**customBinding**，而**BindingConfiguration**屬性設定為使用依賴的自訂通道在支援排序的傳遞，例如 MSMQ 傳輸。</span><span class="sxs-lookup"><span data-stu-id="68a00-376">WCF-Custom adapter: When the **BindingType** property is set to **customBinding**, and the **BindingConfiguration** property is configured to use custom channels that rely on transports supporting ordered delivery such as MSMQ.</span></span>
- <span data-ttu-id="68a00-377">Wcf-customisolated 配接器： 當**BindingType**屬性設定為**customBinding**，而**BindingConfiguration**屬性設定為使用自訂的通道依賴支援排序的傳遞的傳輸。</span><span class="sxs-lookup"><span data-stu-id="68a00-377">WCF-CustomIsolated adapter: When the **BindingType** property is set to **customBinding**, and the **BindingConfiguration** property is configured to use custom channels that rely on transports supporting ordered delivery.</span></span>
- <span data-ttu-id="68a00-378">WCF-NetMsmq 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-378">WCF-NetMsmq adapter</span></span>

<span data-ttu-id="68a00-379">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-379">Type: String</span></span>  
<span data-ttu-id="68a00-380">預設值︰ **False**</span><span class="sxs-lookup"><span data-stu-id="68a00-380">Default value: **False**</span></span>  
<span data-ttu-id="68a00-381">適用於：</span><span class="sxs-lookup"><span data-stu-id="68a00-381">Applies to:</span></span> 
- <span data-ttu-id="68a00-382">WCF-NetMsmq 接收配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-382">WCF-NetMsmq receive adapter</span></span>
- <span data-ttu-id="68a00-383">WCF-Custom 接收配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-383">WCF-Custom receive adapter</span></span>
- <span data-ttu-id="68a00-384">WCF-CustomIsolated 接收配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-384">WCF-CustomIsolated receive adapter</span></span>

#### <a name="outboundbodylocation"></a><span data-ttu-id="68a00-385">OutboundBodyLocation</span><span class="sxs-lookup"><span data-stu-id="68a00-385">OutboundBodyLocation</span></span>
<span data-ttu-id="68a00-386">指定資料選取範圍 soap **主體** 外寄 WCF 訊息的項目。</span><span class="sxs-lookup"><span data-stu-id="68a00-386">Specify the data selection for the SOAP **Body** element of outgoing WCF messages.</span></span> <span data-ttu-id="68a00-387">如需有關如何使用**OutboundBodyLocation**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="68a00-387">For more information about how to use the **OutboundBodyLocation** property, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md).</span></span>

<span data-ttu-id="68a00-388">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-388">Type: String</span></span>  
<span data-ttu-id="68a00-389">預設值： UseBodyElement</span><span class="sxs-lookup"><span data-stu-id="68a00-389">Default value: UseBodyElement</span></span>  

    Applicable values are:
        - UseBodyElement: Use the BizTalk message body part to create the content of the SOAP **Body** element for an outgoing message
        - **UseTem****plate**: Use the template supplied in the OutboundXMLTemplate property to create the content of the SOAP **Body** element for an outgoing message

<span data-ttu-id="68a00-390">適用於： 所有 WCF 配接器*除了*Wcf-netmsmq 接收配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-390">Applies to: All WCF adapters *except* the WCF-NetMsmq receive adapter</span></span>

#### <a name="outboundcustomheaders"></a><span data-ttu-id="68a00-391">OutboundCustomHeaders</span><span class="sxs-lookup"><span data-stu-id="68a00-391">OutboundCustomHeaders</span></span>
<span data-ttu-id="68a00-392">指定外寄訊息的自訂 SOAP 標頭。</span><span class="sxs-lookup"><span data-stu-id="68a00-392">Specify the custom SOAP headers for outgoing messages.</span></span> <span data-ttu-id="68a00-393">使用這個屬性時，屬性必須有\<**標頭**\>元素是根項目。</span><span class="sxs-lookup"><span data-stu-id="68a00-393">When this property is used, the property must have the \<**headers**\> element as the root element.</span></span> <span data-ttu-id="68a00-394">所有自訂 SOAP 標頭必須置於\<**標頭**\>項目。</span><span class="sxs-lookup"><span data-stu-id="68a00-394">All of the custom SOAP headers must be placed inside the \<**headers**\> element.</span></span> <span data-ttu-id="68a00-395">如果自訂 SOAP 標頭值為空字串，您必須指派\<**標頭**\>\</**標頭**\>或\<**標頭**\>給這個屬性。</span><span class="sxs-lookup"><span data-stu-id="68a00-395">If the custom SOAP header value is an empty string, you must assign \<**headers**\>\</**headers**\> or \<**headers**\> to this property.</span></span> <span data-ttu-id="68a00-396">如需如何使用 WCF 配接器使用 SOAP 標頭的詳細資訊，請參閱 SDK 範例，使用自訂 SOAP 標頭使用 WCF 配接器從 [http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960)。</span><span class="sxs-lookup"><span data-stu-id="68a00-396">For more information about how to use SOAP headers with the WCF adapters, see the SDK sample, Using Custom SOAP Headers with the WCF Adapters, from [http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960).</span></span>

<span data-ttu-id="68a00-397">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-397">Type: String</span></span>  
<span data-ttu-id="68a00-398">適用於： 所有 WCF 配接器*除了*Wcf-netmsmq 接收配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-398">Applies to: All WCF adapters *except* the WCF-NetMsmq receive adapter</span></span>

#### <a name="outboundxmltemplate"></a><span data-ttu-id="68a00-399">OutboundXmlTemplate</span><span class="sxs-lookup"><span data-stu-id="68a00-399">OutboundXmlTemplate</span></span>
<span data-ttu-id="68a00-400">指定 XML 格式的範本內容的 SOAP **主體** 外寄訊息的項目。</span><span class="sxs-lookup"><span data-stu-id="68a00-400">Specify the XML-formatted template for the content of the SOAP **Body** element of an outgoing message.</span></span> <span data-ttu-id="68a00-401">如果這個屬性，則需要 **OutboundBodyLocation** 屬性設定為 **UseTemplate**。</span><span class="sxs-lookup"><span data-stu-id="68a00-401">This property is required if the **OutboundBodyLocation** property is set to **UseTemplate**.</span></span> <span data-ttu-id="68a00-402">如需有關如何使用**OutboundXMLTemplate**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="68a00-402">For more information about how to use the **OutboundXMLTemplate** property, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md).</span></span>

<span data-ttu-id="68a00-403">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-403">Type: String</span></span>  
<span data-ttu-id="68a00-404">預設值： 空字串</span><span class="sxs-lookup"><span data-stu-id="68a00-404">Default value: An empty string</span></span>  
<span data-ttu-id="68a00-405">適用於： 所有 WCF 配接器*除了*Wcf-netmsmq 接收配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-405">Applies to: All WCF adapters *except* the WCF-NetMsmq receive adapter</span></span>

#### <a name="password"></a><span data-ttu-id="68a00-406">密碼</span><span class="sxs-lookup"><span data-stu-id="68a00-406">Password</span></span>
<span data-ttu-id="68a00-407">指定要用於驗證目的地伺服器的密碼時 **UseSSO** 屬性設定為 **False**。</span><span class="sxs-lookup"><span data-stu-id="68a00-407">Specify the password to use for authentication with the destination server when the **UseSSO** property is set to **False**.</span></span>

<span data-ttu-id="68a00-408">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-408">Type: String</span></span>  
<span data-ttu-id="68a00-409">預設值： 空字串</span><span class="sxs-lookup"><span data-stu-id="68a00-409">Default value: An empty string</span></span>  
<span data-ttu-id="68a00-410">適用於： 所有 WCF 都傳送配接器*除了*Wcf-netnamedpipe 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-410">Applies to: All WCF send adapters *except* the WCF-NetNamedPipe adapter</span></span>  

#### <a name="propagatefaultmessage"></a><span data-ttu-id="68a00-411">PropagateFaultMessage</span><span class="sxs-lookup"><span data-stu-id="68a00-411">PropagateFaultMessage</span></span>
<span data-ttu-id="68a00-412">指定要傳送或擱置在輸出處理中失敗的訊息。</span><span class="sxs-lookup"><span data-stu-id="68a00-412">Specify whether to route or suspend messages that fail in outbound processing.</span></span> <span data-ttu-id="68a00-413">此屬性只對請求-回應連接埠有效。</span><span class="sxs-lookup"><span data-stu-id="68a00-413">This property is valid only for solicit-response ports.</span></span> 

<span data-ttu-id="68a00-414">**附註**</span><span class="sxs-lookup"><span data-stu-id="68a00-414">**Note**</span></span>  
<span data-ttu-id="68a00-415">您無法使用追蹤設定檔在 BAM 主要匯入資料庫中追蹤這個屬性。</span><span class="sxs-lookup"><span data-stu-id="68a00-415">This property cannot be tracked in the BAM Primary Import database with tracking profiles.</span></span>

<span data-ttu-id="68a00-416">類型：Boolean</span><span class="sxs-lookup"><span data-stu-id="68a00-416">Type: Boolean</span></span>  
<span data-ttu-id="68a00-417">預設值︰ **，則為 True**</span><span class="sxs-lookup"><span data-stu-id="68a00-417">Default value: **True**</span></span>  

    Applicable values are:  
        - True: Route the message that fails outbound processing to a subscribing application (such as another receive port or orchestration schedule)
        - False: Suspend failed messages and generate a negative acknowledgment (NACK)

<span data-ttu-id="68a00-418">適用於： 所有 WCF 都傳送配接器*除了*Wcf-netmsmq 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-418">Applies to: All WCF send adapters *except* the WCF-NetMsmq adapter</span></span>
  
#### <a name="proxyaddress"></a><span data-ttu-id="68a00-419">ProxyAddress</span><span class="sxs-lookup"><span data-stu-id="68a00-419">ProxyAddress</span></span>
<span data-ttu-id="68a00-420">指定 Proxy 伺服器的位址。</span><span class="sxs-lookup"><span data-stu-id="68a00-420">Specify the address of the proxy server.</span></span> <span data-ttu-id="68a00-421">使用 **https** 或 **http** 根據安全性組態的配置。</span><span class="sxs-lookup"><span data-stu-id="68a00-421">Use the **https** or the **http** scheme depending on the security configuration.</span></span> <span data-ttu-id="68a00-422">這個位址後面可以加上冒號和連接埠編號，</span><span class="sxs-lookup"><span data-stu-id="68a00-422">This address can be followed by a colon and the port number.</span></span> <span data-ttu-id="68a00-423">如果需要此屬性， **ProxyToUse**屬性設定為**UserSpecified** (例如 http://127.0.0.1:8080)</span><span class="sxs-lookup"><span data-stu-id="68a00-423">The property is required if the **ProxyToUse** property is set to **UserSpecified** (For example, http://127.0.0.1:8080)</span></span>

<span data-ttu-id="68a00-424">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-424">Type: String</span></span>  
<span data-ttu-id="68a00-425">預設值： 空字串</span><span class="sxs-lookup"><span data-stu-id="68a00-425">Default value: An empty string</span></span>  
<span data-ttu-id="68a00-426">適用於： Wcf-basichttp 傳送配接器、 Wcf-wshttp 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-426">Applies to: WCF-BasicHttp send adapter, WCF-WSHttp send adapter</span></span>  

#### <a name="proxypassword"></a><span data-ttu-id="68a00-427">ProxyPassword</span><span class="sxs-lookup"><span data-stu-id="68a00-427">ProxyPassword</span></span>
<span data-ttu-id="68a00-428">指定要用於指定 proxy 伺服器密碼 **ProxyAddress** 屬性。</span><span class="sxs-lookup"><span data-stu-id="68a00-428">Specify the password to use for the proxy server specified in the **ProxyAddress** property.</span></span>

<span data-ttu-id="68a00-429">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-429">Type: String</span></span>  
<span data-ttu-id="68a00-430">預設值： 空字串</span><span class="sxs-lookup"><span data-stu-id="68a00-430">Default value: An empty string</span></span>  
<span data-ttu-id="68a00-431">適用於： Wcf-basichttp 傳送配接器、 Wcf-wshttp 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-431">Applies to: WCF-BasicHttp send adapter, WCF-WSHttp send adapter</span></span>

#### <a name="proxytouse"></a><span data-ttu-id="68a00-432">ProxyToUse</span><span class="sxs-lookup"><span data-stu-id="68a00-432">ProxyToUse</span></span>
<span data-ttu-id="68a00-433">指定要針對外寄 HTTP 流量使用哪一個 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="68a00-433">Specify which proxy server to use for outgoing HTTP traffic.</span></span>

<span data-ttu-id="68a00-434">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-434">Type: String</span></span>  
<span data-ttu-id="68a00-435">預設值︰ **無**</span><span class="sxs-lookup"><span data-stu-id="68a00-435">Default value: **None**</span></span>  

    Applicable values are:  
        - None: Do not use a proxy server for this send port
        - Default: Use the proxy settings in the send handler hosting this send port
        - UserSpecified: Use the proxy server specified in the **ProxyAddress** property

<span data-ttu-id="68a00-436">適用於： Wcf-basichttp 傳送配接器、 Wcf-wshttp 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-436">Applies to: WCF-BasicHttp send adapter, WCF-WSHttp send adapter</span></span>  

#### <a name="proxyusername"></a><span data-ttu-id="68a00-437">ProxyUserName</span><span class="sxs-lookup"><span data-stu-id="68a00-437">ProxyUserName</span></span>
<span data-ttu-id="68a00-438">指定要用於指定 proxy 伺服器的使用者名稱 **ProxyAddress** 屬性。</span><span class="sxs-lookup"><span data-stu-id="68a00-438">Specify the user name to use for the proxy server specified in the **ProxyAddress** property.</span></span> <span data-ttu-id="68a00-439">此屬性為必要的如果 **ProxyToUse** 屬性設定為 **UserSpecified**。</span><span class="sxs-lookup"><span data-stu-id="68a00-439">The property is required if the **ProxyToUse** property is set to **UserSpecified**.</span></span>

<span data-ttu-id="68a00-440">如需有關這個屬性的詳細資訊，請參閱[如何設定 Wcf-wshttp 傳送埠](../core/how-to-configure-a-wcf-wshttp-send-port.md)和[如何設定 Wcf-basichttp 傳送埠](http://msdn.microsoft.com/library/acdb50fa-57fe-4657-9561-b6b2f4919c7f)。</span><span class="sxs-lookup"><span data-stu-id="68a00-440">For more information about this property, see [How to Configure a WCF-WSHttp Send Port](../core/how-to-configure-a-wcf-wshttp-send-port.md) and [How to Configure a WCF-BasicHttp Send Port](http://msdn.microsoft.com/library/acdb50fa-57fe-4657-9561-b6b2f4919c7f).</span></span>

<span data-ttu-id="68a00-441">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-441">Type: String</span></span>  
<span data-ttu-id="68a00-442">適用於： Wcf-basichttp 傳送配接器、 Wcf-wshttp 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-442">Applies to: WCF-BasicHttp send adapter, WCF-WSHttp send adapter</span></span>

#### <a name="replytoaddress"></a><span data-ttu-id="68a00-443">ReplyToAddress</span><span class="sxs-lookup"><span data-stu-id="68a00-443">ReplyToAddress</span></span>
<span data-ttu-id="68a00-444">指出外寄 WCF 訊息的回應端點位址，這些訊息對應於透過要求-回應接收位置接收的內送訊息。</span><span class="sxs-lookup"><span data-stu-id="68a00-444">Indicate the reply endpoint address for the outgoing WCF messages corresponding to incoming messages received through the request-response receive locations.</span></span> <span data-ttu-id="68a00-445">此屬性會自動從內送訊息升級。</span><span class="sxs-lookup"><span data-stu-id="68a00-445">The property is automatically promoted from incoming messages.</span></span>

<span data-ttu-id="68a00-446">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-446">Type: String</span></span>  
<span data-ttu-id="68a00-447">預設值： 空字串</span><span class="sxs-lookup"><span data-stu-id="68a00-447">Default value: An empty string</span></span>  
<span data-ttu-id="68a00-448">適用於： 所有 WCF 配接器*除了*Wcf-netmsmq 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-448">Applies to: All WCF adapters *except* the WCF-NetMsmq adapter</span></span>

#### <a name="securitymode"></a><span data-ttu-id="68a00-449">SecurityMode</span><span class="sxs-lookup"><span data-stu-id="68a00-449">SecurityMode</span></span>
<span data-ttu-id="68a00-450">指定使用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="68a00-450">Specify the type of security that is used.</span></span> <span data-ttu-id="68a00-451">每個 WCF 配接器適用的值都不一樣。</span><span class="sxs-lookup"><span data-stu-id="68a00-451">The applicable values differ for each WCF adapter.</span></span> <span data-ttu-id="68a00-452">如需有關**SecurityMode**屬性，請參閱使用說明主題中的每個 WCF 配接器[WCF 配接器](../core/wcf-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="68a00-452">For more information about the **SecurityMode** property, see how-to topics for each WCF adapter in [WCF Adapters](../core/wcf-adapters.md).</span></span> 

<span data-ttu-id="68a00-453">**附註**</span><span class="sxs-lookup"><span data-stu-id="68a00-453">**Note**</span></span>  
<span data-ttu-id="68a00-454">您無法使用追蹤設定檔在 BAM 主要匯入資料庫中追蹤這個屬性。</span><span class="sxs-lookup"><span data-stu-id="68a00-454">This property cannot be tracked in the BAM Primary Import database with tracking profiles.</span></span>

<span data-ttu-id="68a00-455">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-455">Type: String</span></span>  
<span data-ttu-id="68a00-456">適用於： 所有 WCF 配接器*除了*Wcf-custom 和 Wcf-customisolated 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-456">Applies to: All WCF adapters *except* the WCF-Custom and WCF-CustomIsolated adapters</span></span>

#### <a name="sendtimeout"></a><span data-ttu-id="68a00-457">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="68a00-457">SendTimeout</span></span>
<span data-ttu-id="68a00-458">指定時間值，表示可供完成傳送作業的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="68a00-458">Specify a time span value that indicates the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="68a00-459">這個值會指定完成整個互動的時間長度，即使對應方傳送很大的訊息也是如此。</span><span class="sxs-lookup"><span data-stu-id="68a00-459">This value specifies a time span for the whole interaction to complete, even if the correspondent sends a large message.</span></span>

<span data-ttu-id="68a00-460">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-460">Type: String</span></span>  
<span data-ttu-id="68a00-461">預設值：00:01:00</span><span class="sxs-lookup"><span data-stu-id="68a00-461">Default value: 00:01:00</span></span>  
<span data-ttu-id="68a00-462">適用於： 所有 WCF 配接器*除了*Wcf-custom 和 Wcf-customisolated 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-462">Applies to: All WCF adapters *except* the WCF-Custom and WCF-CustomIsolated adapters</span></span>

#### <a name="servicebehaviorconfiguration"></a><span data-ttu-id="68a00-463">ServiceBehaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="68a00-463">ServiceBehaviorConfiguration</span></span>
<span data-ttu-id="68a00-464">指定的 XML 字串**\<行為\>** 元素**\<serviceBehaviors\>** 設定 WCF 行為設定的項目服務。</span><span class="sxs-lookup"><span data-stu-id="68a00-464">Specify an XML string with the **\<behavior\>** element of the **\<serviceBehaviors\>** element to configure the behavior settings of a WCF service.</span></span> <span data-ttu-id="68a00-465">如需有關**\<serviceBehaviors\>** 項目，請參閱 < 另請參閱中的適當主題。</span><span class="sxs-lookup"><span data-stu-id="68a00-465">For more information about the **\<serviceBehaviors\>** element, see the appropriate topic in See Also.</span></span>

<span data-ttu-id="68a00-466">範例：</span><span class="sxs-lookup"><span data-stu-id="68a00-466">Example:</span></span>

```
<behavior name="SampleServiceBehavior">
<serviceAuthorization principalPermissionMode="UseAspNetRoles"/>
<serviceCredentials>
<serviceCertificate findValue="539d9ab3089bb6dc187fa7dbb382cf01f8d78f5f" storeLocation="CurrentUser" x509FindType="FindByThumbprint"/>
</serviceCredentials>
<serviceMetadata httpGetEnabled="true"/>
</behavior>
```

<span data-ttu-id="68a00-467">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-467">Type: String</span></span>  
<span data-ttu-id="68a00-468">預設值： 空字串</span><span class="sxs-lookup"><span data-stu-id="68a00-468">Default value: An empty string</span></span>  
<span data-ttu-id="68a00-469">適用於： Wcf-custom 接收配接器，Wcf-customisolated 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-469">Applies to: WCF-Custom receive adapter, WCF-CustomIsolated adapter</span></span>

#### <a name="servicecertificate"></a><span data-ttu-id="68a00-470">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="68a00-470">ServiceCertificate</span></span>
<span data-ttu-id="68a00-471">如果將這個屬性用於接收位置，請針對用戶端驗證服務時所使用的接收位置，指定 X.509 憑證的指紋。</span><span class="sxs-lookup"><span data-stu-id="68a00-471">If this property is used for receive locations, specify the thumbprint of the X.509 certificate for the receive locations that clients use to authenticate the service.</span></span> <span data-ttu-id="68a00-472">要用於此屬性的憑證必須安裝到 **我** 存放 **目前使用者** 位置。</span><span class="sxs-lookup"><span data-stu-id="68a00-472">The certificate to be used for this property must be installed into the **My** store in the **Current User** location.</span></span>

<span data-ttu-id="68a00-473">如果將這個屬性用於傳送埠，請指定 X.509 憑證的指紋，以驗證此傳送埠傳送訊息的目標服務。</span><span class="sxs-lookup"><span data-stu-id="68a00-473">If this property is used for send ports, specify the thumbprint of the X.509 certificate for authenticating the service to which this send port sends messages.</span></span> <span data-ttu-id="68a00-474">要用於此屬性的憑證必須安裝到 **其他人** 存放 **本機** 位置。</span><span class="sxs-lookup"><span data-stu-id="68a00-474">The certificate to be used for this property must be installed into the **Other People** store in the **Local Machine** location.</span></span>

<span data-ttu-id="68a00-475">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-475">Type: String</span></span>  
<span data-ttu-id="68a00-476">預設值： 空字串</span><span class="sxs-lookup"><span data-stu-id="68a00-476">Default value: An empty string</span></span>  
<span data-ttu-id="68a00-477">適用於：</span><span class="sxs-lookup"><span data-stu-id="68a00-477">Applies to:</span></span> 
- <span data-ttu-id="68a00-478">WCF-BasicHttp 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-478">WCF-BasicHttp adapter</span></span>
- <span data-ttu-id="68a00-479">WCF-NetMsmq 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-479">WCF-NetMsmq adapter</span></span>
- <span data-ttu-id="68a00-480">WCF-WSHttp 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-480">WCF-WSHttp adapter</span></span>
- <span data-ttu-id="68a00-481">WCF-NetTcp 接收配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-481">WCF-NetTcp receive adapter</span></span>

#### <a name="suspendmessageonfailure"></a><span data-ttu-id="68a00-482">SuspendMessageOnFailure</span><span class="sxs-lookup"><span data-stu-id="68a00-482">SuspendMessageOnFailure</span></span>
<span data-ttu-id="68a00-483">指定是否擱置因接收管線失敗或路由失敗而造成輸入處理失敗的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="68a00-483">Specify whether to suspend the request message that fails inbound processing due to a receive pipeline failure or a routing failure.</span></span>

<span data-ttu-id="68a00-484">類型：Boolean</span><span class="sxs-lookup"><span data-stu-id="68a00-484">Type: Boolean</span></span>  
<span data-ttu-id="68a00-485">預設值：True</span><span class="sxs-lookup"><span data-stu-id="68a00-485">Default value: True</span></span>  
<span data-ttu-id="68a00-486">適用於： 所有 WCF 都接收配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-486">Applies to: All WCF receive adapters</span></span>  

#### <a name="textencoding"></a><span data-ttu-id="68a00-487">TextEncoding</span><span class="sxs-lookup"><span data-stu-id="68a00-487">TextEncoding</span></span>
<span data-ttu-id="68a00-488">指定字元集的編碼方式來繫結上發出訊息時 **MessageEncoding** 屬性設定為 **文字**。</span><span class="sxs-lookup"><span data-stu-id="68a00-488">Specify the character set encoding to be used for emitting messages on the binding when the **MessageEncoding** property is set to **Text**.</span></span> 

<span data-ttu-id="68a00-489">**附註**</span><span class="sxs-lookup"><span data-stu-id="68a00-489">**Note**</span></span>  
<span data-ttu-id="68a00-490">您無法使用追蹤設定檔在 BAM 主要匯入資料庫中追蹤這個屬性。</span><span class="sxs-lookup"><span data-stu-id="68a00-490">This property cannot be tracked in the BAM Primary Import database with tracking profiles.</span></span> 

<span data-ttu-id="68a00-491">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-491">Type: String</span></span>  
<span data-ttu-id="68a00-492">預設值： utf-8</span><span class="sxs-lookup"><span data-stu-id="68a00-492">Default value: utf-8</span></span>  

    Applicable values are:  
        - unicodeFFF: Unicode BigEndian encoding
        - utf-16: 16-bit encoding
        - utf-8: 8-bit encoding

<span data-ttu-id="68a00-493">適用於： Wcf-basichttp 配接器、 Wcf-wshttp 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-493">Applies to: WCF-BasicHttp adapter, WCF-WSHttp adapter</span></span>
  
#### <a name="timetolive"></a><span data-ttu-id="68a00-494">TimeToLive</span><span class="sxs-lookup"><span data-stu-id="68a00-494">TimeToLive</span></span>
<span data-ttu-id="68a00-495">指定訊息在過期並置入無效信件佇列之前的有效時間有多長。</span><span class="sxs-lookup"><span data-stu-id="68a00-495">Specify a time span for how long the messages are valid before they are expired and put into the dead-letter queue.</span></span> <span data-ttu-id="68a00-496">設定這個屬性可確保講求時效的訊息，在經過傳送埠處理之後才會變成過時訊息。</span><span class="sxs-lookup"><span data-stu-id="68a00-496">This property is set to ensure that time-sensitive messages do not become stale before they are processed by a send port.</span></span> <span data-ttu-id="68a00-497">在佇列中的訊息，若是沒有在指定的時間間隔內由此傳送埠耗用，便會被視為過期。</span><span class="sxs-lookup"><span data-stu-id="68a00-497">A message in a queue that is not consumed by this send port within the time interval specified is said to be expired.</span></span> <span data-ttu-id="68a00-498">過期的訊息會傳送到特殊的佇列，稱為無法寄出的信件佇列。</span><span class="sxs-lookup"><span data-stu-id="68a00-498">Expired messages are sent to special queue called the dead-letter queue.</span></span> <span data-ttu-id="68a00-499">寄不出信件佇列的位置會設定與 **DeadLetterQueue** 屬性。</span><span class="sxs-lookup"><span data-stu-id="68a00-499">The location of the dead-letter queue is set with the **DeadLetterQueue** property.</span></span>

<span data-ttu-id="68a00-500">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-500">Type: String</span></span>  
<span data-ttu-id="68a00-501">預設值︰ 1.00:00:00</span><span class="sxs-lookup"><span data-stu-id="68a00-501">Default value: 1.00:00:00</span></span>  
<span data-ttu-id="68a00-502">適用於： Wcf-netmsmq 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-502">Applies to: WCF-NetMsmq send adapter</span></span>

#### <a name="to"></a><span data-ttu-id="68a00-503">若要</span><span class="sxs-lookup"><span data-stu-id="68a00-503">To</span></span>
<span data-ttu-id="68a00-504">指定 WCF 傳送埠傳送之外寄 WCF 訊息的目的端點位址。</span><span class="sxs-lookup"><span data-stu-id="68a00-504">Specify the destination endpoint address for outgoing WCF messages that the WCF send ports send.</span></span>

<span data-ttu-id="68a00-505">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-505">Type: String</span></span>  
<span data-ttu-id="68a00-506">預設值： 空字串</span><span class="sxs-lookup"><span data-stu-id="68a00-506">Default value: An empty string</span></span>  
<span data-ttu-id="68a00-507">適用於： 所有 WCF 都傳送配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-507">Applies to: All WCF send adapters</span></span>  

#### <a name="transactionprotocol"></a><span data-ttu-id="68a00-508">TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="68a00-508">TransactionProtocol</span></span>
<span data-ttu-id="68a00-509">指定要搭配此繫結使用的交易通訊協定。</span><span class="sxs-lookup"><span data-stu-id="68a00-509">Specify the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="68a00-510">如果這個屬性，則需要 **EnableTransaction** 屬性設定為 **True**。</span><span class="sxs-lookup"><span data-stu-id="68a00-510">This property is required if the **EnableTransaction** property is set to **True**.</span></span>

<span data-ttu-id="68a00-511">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-511">Type: String</span></span>  
<span data-ttu-id="68a00-512">預設值： OleTransaction</span><span class="sxs-lookup"><span data-stu-id="68a00-512">Default value: OleTransaction</span></span>  

    Applicable values are: OleTransaction, WS-AtomicTransaction

<span data-ttu-id="68a00-513">適用於： Wcf-netnamedpipe 配接器，Wcf-nettcp 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-513">Applies to: WCF-NetNamedPipe adapter,  WCF-NetTcp adapter</span></span>  

#### <a name="transportclientcredentialtype"></a><span data-ttu-id="68a00-514">TransportClientCredentialType</span><span class="sxs-lookup"><span data-stu-id="68a00-514">TransportClientCredentialType</span></span>
<span data-ttu-id="68a00-515">指定在執行傳送埠驗證時，所要使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="68a00-515">Specify the type of credential to be used when performing the send port authentication.</span></span> <span data-ttu-id="68a00-516">每個 WCF 配接器適用的值都不一樣。</span><span class="sxs-lookup"><span data-stu-id="68a00-516">The applicable values differ for each WCF adapter.</span></span> <span data-ttu-id="68a00-517">如需有關**TransportClientCredentialType**屬性，請參閱使用說明主題中的每個 WCF 配接器[WCF 配接器](../core/wcf-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="68a00-517">For more information about the **TransportClientCredentialType** property, see how-to topics for each WCF adapter in [WCF Adapters](../core/wcf-adapters.md).</span></span>

<span data-ttu-id="68a00-518">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-518">Type: String</span></span>  
<span data-ttu-id="68a00-519">適用於： Wcf-basic 配接器、 Wcf-nettcp 配接器、 Wcf-wshttp 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-519">Applies to: WCF-Basic adapter, WCF-NetTcp adapter, WCF-WSHttp adapter</span></span>  

#### <a name="transportprotectionlevel"></a><span data-ttu-id="68a00-520">TransportProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="68a00-520">TransportProtectionLevel</span></span>
<span data-ttu-id="68a00-521">指定在 TCP 傳輸層的安全性。</span><span class="sxs-lookup"><span data-stu-id="68a00-521">Specify security at the level of the TCP transport.</span></span> <span data-ttu-id="68a00-522">簽署訊息可以降低訊息在傳輸時遭到第三者竄改的風險。</span><span class="sxs-lookup"><span data-stu-id="68a00-522">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="68a00-523">加密可在傳輸時提供資料等級的隱私權。</span><span class="sxs-lookup"><span data-stu-id="68a00-523">Encryption provides data-level privacy during transport.</span></span>

<span data-ttu-id="68a00-524">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-524">Type: String</span></span>  
<span data-ttu-id="68a00-525">預設值︰ **EncryptAndSign**</span><span class="sxs-lookup"><span data-stu-id="68a00-525">Default value: **EncryptAndSign**</span></span>  

    Applicable values are:  
        - None: No protection
        - Sign: Messages are signed
        - EncryptAndSign: Messages are encrypted and signed

<span data-ttu-id="68a00-526">適用於： Wcf-nettcp 配接器，Wcf-netnamedpipe 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-526">Applies to: WCF-NetTcp adapter, WCF-NetNamedPipe adapter</span></span>  

#### <a name="username"></a><span data-ttu-id="68a00-527">UserName</span><span class="sxs-lookup"><span data-stu-id="68a00-527">UserName</span></span>
<span data-ttu-id="68a00-528">指定要用於目的地伺服器驗證的使用者名稱時 **UseSSO** 屬性設定為 **False**。</span><span class="sxs-lookup"><span data-stu-id="68a00-528">Specify the user name to use for authentication with the destination server when the **UseSSO** property is set to **False**.</span></span> <span data-ttu-id="68a00-529">您不需要對此屬性使用 domain\user 格式。</span><span class="sxs-lookup"><span data-stu-id="68a00-529">You do not have to use the domain\user format for this property.</span></span>

<span data-ttu-id="68a00-530">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-530">Type: String</span></span>  
<span data-ttu-id="68a00-531">預設值： 空字串</span><span class="sxs-lookup"><span data-stu-id="68a00-531">Default value: An empty string</span></span>  
<span data-ttu-id="68a00-532">適用於： 所有 WCF 都傳送配接器*除了*Wcf-netnamedpipe 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-532">Applies to: All WCF send adapters *except* the WCF-NetNamedPipe adapter</span></span>

#### <a name="usesourcejournal"></a><span data-ttu-id="68a00-533">UseSourceJournal</span><span class="sxs-lookup"><span data-stu-id="68a00-533">UseSourceJournal</span></span>
<span data-ttu-id="68a00-534">指定由此傳送埠處理的訊息複本是否應該存放在來源日誌佇列中。</span><span class="sxs-lookup"><span data-stu-id="68a00-534">Specify whether copies of messages processed by this send port should be stored in the source journal queue.</span></span>

<span data-ttu-id="68a00-535">類型：Boolean</span><span class="sxs-lookup"><span data-stu-id="68a00-535">Type: Boolean</span></span>  
<span data-ttu-id="68a00-536">預設值：False</span><span class="sxs-lookup"><span data-stu-id="68a00-536">Default value: False</span></span>  
<span data-ttu-id="68a00-537">適用於： Wcf-netmsmq 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-537">Applies to: WCF-NetMsmq send adapter</span></span>  

#### <a name="usesso"></a><span data-ttu-id="68a00-538">UseSSO</span><span class="sxs-lookup"><span data-stu-id="68a00-538">UseSSO</span></span>
<span data-ttu-id="68a00-539">대상 서버 인증을 위한 클라이언트 자격 증명을 검색하는 데 Single Sign-On을 사용할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="68a00-539">Specify whether to use Single Sign-On to retrieve client credentials for authentication with the destination server.</span></span> 

<span data-ttu-id="68a00-540">**附註**</span><span class="sxs-lookup"><span data-stu-id="68a00-540">**Note**</span></span>  
<span data-ttu-id="68a00-541">您無法使用追蹤設定檔在 BAM 主要匯入資料庫中追蹤這個屬性。</span><span class="sxs-lookup"><span data-stu-id="68a00-541">This property cannot be tracked in the BAM Primary Import database with tracking profiles.</span></span> 

<span data-ttu-id="68a00-542">類型：Boolean</span><span class="sxs-lookup"><span data-stu-id="68a00-542">Type: Boolean</span></span>  
<span data-ttu-id="68a00-543">預設值：False</span><span class="sxs-lookup"><span data-stu-id="68a00-543">Default value: False</span></span>  
<span data-ttu-id="68a00-544">適用於： 所有 WCF 都傳送配接器*除了*Wcf-netnamedpipe 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-544">Applies to: All WCF send adapters *except* the WCF-NetNamedPipe adapter</span></span>

#### <a name="referencedbindings"></a><span data-ttu-id="68a00-545">ReferencedBindings</span><span class="sxs-lookup"><span data-stu-id="68a00-545">ReferencedBindings</span></span>
<span data-ttu-id="68a00-546">指定所參考的繫結組態**bindingConfiguration**屬性**\<簽發者\>** 元素**wsFederationHttpBinding**和**customBinding**，表示安全性權杖服務 (STS) 發行安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="68a00-546">Specify the binding configurations referenced by the **bindingConfiguration** attribute of the **\<issuer\>** element for the **wsFederationHttpBinding** and **customBinding**, which indicates the Security Token Service (STS) that issues security tokens.</span></span> <span data-ttu-id="68a00-547">如需詳細資訊**\<簽發者\>** 項目，請參閱主題 <"\<簽發者\>」 在[http://go.microsoft.com/fwlink/?LinkId=83476](http://go.microsoft.com/fwlink/?LinkId=83476)。</span><span class="sxs-lookup"><span data-stu-id="68a00-547">For more information about the **\<issuer\>** element, see the topic, "\<issuer\>" at [http://go.microsoft.com/fwlink/?LinkId=83476](http://go.microsoft.com/fwlink/?LinkId=83476).</span></span>

<span data-ttu-id="68a00-548">繫結資訊，包括**\<簽發者\>** 元素**wsFederationHttpBinding**和**customBinding**可以是透過設定**BindingConfiguration** Wcf-custom 和 Wcf-customisolated 配接器的屬性。</span><span class="sxs-lookup"><span data-stu-id="68a00-548">The binding information including the **\<issuer\>** element for the **wsFederationHttpBinding** and **customBinding** can be configured through the **BindingConfiguration** property of the WCF-Custom and WCF-CustomIsolated adapters.</span></span> <span data-ttu-id="68a00-549">所有參考繫結組態，這個屬性必須放置在表單的[\<繫結\>](http://go.microsoft.com/fwlink/?LinkID=80878)項目。</span><span class="sxs-lookup"><span data-stu-id="68a00-549">All of the referenced binding configurations for this property must be placed in the form of the [\<bindings\>](http://go.microsoft.com/fwlink/?LinkID=80878) element.</span></span> 

<span data-ttu-id="68a00-550">**附註**</span><span class="sxs-lookup"><span data-stu-id="68a00-550">**Note**</span></span>  
<span data-ttu-id="68a00-551">**BindingConfiguration**屬性**\<簽發者\>** 元素必須參考這個屬性中的有效繫結名稱。</span><span class="sxs-lookup"><span data-stu-id="68a00-551">The **bindingConfiguration** attribute of the **\<issuer\>** element must refer to a valid binding name in this property.</span></span> 

<span data-ttu-id="68a00-552">**附註**</span><span class="sxs-lookup"><span data-stu-id="68a00-552">**Note**</span></span>  
<span data-ttu-id="68a00-553">**\<簽發者\>** 中參考繫結組態項目也可以使用參照到不同的繫結中設定這個屬性如果這個參考鏈結不會循環相依性。</span><span class="sxs-lookup"><span data-stu-id="68a00-553">The **\<issuer\>** element in the referenced binding configurations can also refer to a different binding configuration in this property if this reference chain does not make a circular dependency.</span></span> 

<span data-ttu-id="68a00-554">範例：</span><span class="sxs-lookup"><span data-stu-id="68a00-554">Example:</span></span> 

```
WCF.BindingConfiguration = @"<wsFederationHttpBinding>
<binding name=""sampleBinding"">
<security mode=""Message"">
<message issuedKeyType=""AsymmetricKey"">
<issuer address=""http://www.contoso.com/samplests"" binding=""wsFederationHttpBinding"" bindingConfiguration=""**contosoSTSBinding**""/>
</message>
</security>
</binding>
</wsFederationHttpBinding>";
WCF.ReferencedBinding =@"<bindings>
<wsFederationHttpBinding>
<binding name=""**contosoSTSBinding**"">
<security mode=""Message"">
<message negotiateServiceCredential=""false"">
<issuer address=""http://northwind.com/samplests"" bindingConfiguration=""**northwindBinding**"" binding=""wsHttpBinding"">
</issuer>
</message>
</security>
</binding>
</wsFederationHttpBinding>
<wsHttpBinding>
<binding name=""**northwindBinding**"">
<security mode=""Message"">
<message clientCredentialType=""Certificate""/>
</security>
</binding>
</wsHttpBinding>
</bindings>" 
``` 

<span data-ttu-id="68a00-555">**附註**</span><span class="sxs-lookup"><span data-stu-id="68a00-555">**Note**</span></span>  
<span data-ttu-id="68a00-556">**ReferencedBinding**屬性不能包含中使用的繫結組態**BindingConfiguration**屬性。</span><span class="sxs-lookup"><span data-stu-id="68a00-556">**ReferencedBinding** property must not contain the binding configuration used in the **BindingConfiguration** property.</span></span>

<span data-ttu-id="68a00-557">유형: 문자열</span><span class="sxs-lookup"><span data-stu-id="68a00-557">Type: String</span></span>  
<span data-ttu-id="68a00-558">預設值： 空字串</span><span class="sxs-lookup"><span data-stu-id="68a00-558">Default value: An empty string</span></span>  
<span data-ttu-id="68a00-559">適用於： Wcf-custom 配接器，Wcf-customisolated 配接器</span><span class="sxs-lookup"><span data-stu-id="68a00-559">Applies to: WCF-Custom adapter, WCF-CustomIsolated adapter</span></span>
  
## <a name="see-also"></a><span data-ttu-id="68a00-560">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68a00-560">See Also</span></span>  
 <span data-ttu-id="68a00-561">[WCF 配接器](../core/wcf-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="68a00-561">[WCF Adapters](../core/wcf-adapters.md) </span></span>  
 <span data-ttu-id="68a00-562">[\<行為\>的\<endpointBehaviors\>](http://go.microsoft.com/fwlink/?LinkId=80879) </span><span class="sxs-lookup"><span data-stu-id="68a00-562">[\<behavior\> of \<endpointBehaviors\>](http://go.microsoft.com/fwlink/?LinkId=80879) </span></span>  
 <span data-ttu-id="68a00-563">[\<bindings\>](http://go.microsoft.com/fwlink/?LinkId=80878) </span><span class="sxs-lookup"><span data-stu-id="68a00-563">[\<bindings\>](http://go.microsoft.com/fwlink/?LinkId=80878) </span></span>  
 <span data-ttu-id="68a00-564">[\<behavior\> of \<serviceBehaviors\>](http://go.microsoft.com/fwlink/?LinkId=81095) </span><span class="sxs-lookup"><span data-stu-id="68a00-564">[\<behavior\> of \<serviceBehaviors\>](http://go.microsoft.com/fwlink/?LinkId=81095) </span></span>  
 <span data-ttu-id="68a00-565">[依序傳遞訊息](../core/ordered-delivery-of-messages.md) </span><span class="sxs-lookup"><span data-stu-id="68a00-565">[Ordered Delivery of Messages](../core/ordered-delivery-of-messages.md) </span></span>  
 [<span data-ttu-id="68a00-566">負載平衡</span><span class="sxs-lookup"><span data-stu-id="68a00-566">Load Balancing</span></span>](http://go.microsoft.com/fwlink/?LinkId=81089)
