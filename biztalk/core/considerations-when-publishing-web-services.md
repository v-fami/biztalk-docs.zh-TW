---
title: Web 服務發佈時的考量 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- schemas, publishing
- Web services, planning
- Web services, schemas
- schemas, Web services
ms.assetid: 3ace0260-a1cb-4e59-a820-36ee7d5cceda
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb9ef5d7dd2e035caaa1981129eae5ac4b51ac71
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014775"
---
# <a name="considerations-when-publishing-web-services"></a><span data-ttu-id="d91b5-102">發佈 Web 服務的考量</span><span class="sxs-lookup"><span data-stu-id="d91b5-102">Considerations When Publishing Web Services</span></span>
<span data-ttu-id="d91b5-103">本主題提供發佈 Web 服務之前應考量的資訊。</span><span class="sxs-lookup"><span data-stu-id="d91b5-103">This topic provides information that you should consider before you publish your Web services.</span></span>  
  
## <a name="publishing-schemas-and-the-include-element"></a><span data-ttu-id="d91b5-104">發佈結構描述和 include 項目</span><span class="sxs-lookup"><span data-stu-id="d91b5-104">Publishing schemas and the include element</span></span>  
 <span data-ttu-id="d91b5-105">少數的情況下，所包含的結構描述所在**包括**項目不能發行為 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="d91b5-105">There are a few scenarios where schemas that contain the **include** element cannot be published as a Web service.</span></span> <span data-ttu-id="d91b5-106">因此當您完成 [BizTalk Web 服務發佈精靈] 時，將會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="d91b5-106">An error will occur when you complete the BizTalk Web Services Publishing Wizard.</span></span> <span data-ttu-id="d91b5-107">這些限制包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="d91b5-107">These restrictions include the following:</span></span>  
  
- <span data-ttu-id="d91b5-108">循環包含 (包含結構描述已**包括**要包含的結構描述項目)</span><span class="sxs-lookup"><span data-stu-id="d91b5-108">Circular includes (the included schema has an **include** element to the including schema)</span></span>  
  
- <span data-ttu-id="d91b5-109">無法解析**schemaLocation**屬性會造成錯誤</span><span class="sxs-lookup"><span data-stu-id="d91b5-109">An unresolved **schemaLocation** attribute will cause an error</span></span>  
  
  <span data-ttu-id="d91b5-110">如需有關限制的包含項目，請參閱 < 包含的項目繫結支援 >，網址[ http://go.microsoft.com/fwlink/?LinkId=62312 ](http://go.microsoft.com/fwlink/?LinkId=62312)。</span><span class="sxs-lookup"><span data-stu-id="d91b5-110">For more information about the limitation of include element, see "Include Element Binding Support" at [http://go.microsoft.com/fwlink/?LinkId=62312](http://go.microsoft.com/fwlink/?LinkId=62312).</span></span>  
  
## <a name="publishing-schemas-and-the-import-element"></a><span data-ttu-id="d91b5-111">發佈結構描述和 import 項目</span><span class="sxs-lookup"><span data-stu-id="d91b5-111">Publishing schemas and the import element</span></span>  
 <span data-ttu-id="d91b5-112">[BizTalk Web 服務發佈精靈] 與 .NET Framework 中包含的 XSD.exe 擁有相同的限制。</span><span class="sxs-lookup"><span data-stu-id="d91b5-112">BizTalk Web Services Publishing Wizard has the same limitation as XSD.exe included in .NET Framework.</span></span> <span data-ttu-id="d91b5-113">詳細資訊，請參閱 < 匯入項目繫結支援 >，網址[ http://go.microsoft.com/fwlink/?LinkId=62311 ](http://go.microsoft.com/fwlink/?LinkId=62311)。</span><span class="sxs-lookup"><span data-stu-id="d91b5-113">For more information, see "Import Element Binding Support" at [http://go.microsoft.com/fwlink/?LinkId=62311](http://go.microsoft.com/fwlink/?LinkId=62311).</span></span>  
  
## <a name="publishing-schemas-and-the-redefine-element"></a><span data-ttu-id="d91b5-114">發佈結構描述和 redefine 項目</span><span class="sxs-lookup"><span data-stu-id="d91b5-114">Publishing schemas and the redefine element</span></span>  
 <span data-ttu-id="d91b5-115">[BizTalk Web 服務發佈精靈] 與 .NET Framework 中包含的 XSD.exe 擁有相同的限制。</span><span class="sxs-lookup"><span data-stu-id="d91b5-115">BizTalk Web Services Publishing Wizard has the same limitation as XSD.exe included in .NET Framework.</span></span> <span data-ttu-id="d91b5-116">詳細資訊，請參閱 < Redefine 項目繫結支援 >，網址[ http://go.microsoft.com/fwlink/?LinkId=62313 ](http://go.microsoft.com/fwlink/?LinkId=62313)。</span><span class="sxs-lookup"><span data-stu-id="d91b5-116">For more information, see "Redefine Element Binding Support" at [http://go.microsoft.com/fwlink/?LinkId=62313](http://go.microsoft.com/fwlink/?LinkId=62313).</span></span>  
  
## <a name="publishing-schemas-that-specify-values-for-minoccurs-or-maxoccurs-attributes"></a><span data-ttu-id="d91b5-117">發佈指定 minOccurs 或 maxOccurs 屬性值的結構描述</span><span class="sxs-lookup"><span data-stu-id="d91b5-117">Publishing schemas that specify values for minOccurs or maxOccurs attributes</span></span>  
 <span data-ttu-id="d91b5-118">如果您將發佈包含結構描述**minOccurs**或是**maxOccurs**具有特定值的屬性，這些值可能不同於已發行的 Web 服務所公開的結構描述。</span><span class="sxs-lookup"><span data-stu-id="d91b5-118">If you publish a schema that contains **minOccurs** or **maxOccurs** attributes with specific values, these values may be different in schema exposed by the published Web service.</span></span> <span data-ttu-id="d91b5-119">一般的基本原則是，所有 minOccurs 屬性都會轉換成 0 (minOccurs=0)，而 maxOccurs 屬性會轉換成 1 或未繫結 (maxOccurs=1 或 maxOccurs=unbounded)。</span><span class="sxs-lookup"><span data-stu-id="d91b5-119">As a general rule of thumb, all minOccurs attributes are converted to 0 (minOccurs=0) and maxOccurs attributes are converted to either 1 or unbounded (maxOccurs=1 or maxOccurs=unbounded).</span></span>  
  
## <a name="publishing-envelope-schemas"></a><span data-ttu-id="d91b5-120">發佈信封結構描述</span><span class="sxs-lookup"><span data-stu-id="d91b5-120">Publishing envelope schemas</span></span>  
 <span data-ttu-id="d91b5-121">如果您有將要發佈為 Web 服務的信封結構描述，則必須手動修改產生的 Web 專案。</span><span class="sxs-lookup"><span data-stu-id="d91b5-121">If you have an envelop schema that you are publishing as a Web service, you need to manually modify the generated Web project.</span></span>  
  
#### <a name="to-modify-the-generated-web-project-for-envelope-schemas"></a><span data-ttu-id="d91b5-122">若要針對信封結構描述修改所產生的 Web 專案</span><span class="sxs-lookup"><span data-stu-id="d91b5-122">To modify the generated Web project for envelope schemas</span></span>  
  
1.  <span data-ttu-id="d91b5-123">開啟 <`myWebService`>.asmx.cs 檔。</span><span class="sxs-lookup"><span data-stu-id="d91b5-123">Open the <`myWebService`>.asmx.cs file.</span></span>  
  
2.  <span data-ttu-id="d91b5-124">編輯檔案並且將 `bodyTypeAssemblyQualifiedName = <dll.name.version.>` 變更為 `bodyTypeAssemblyQualifiedName = null`。</span><span class="sxs-lookup"><span data-stu-id="d91b5-124">Edit the file and change `bodyTypeAssemblyQualifiedName = <dll.name.version.>` to `bodyTypeAssemblyQualifiedName = null`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d91b5-125">如果先前的 .dll 檔案仍存在於 ASP.NET 背景工作處理序中，您可能需要重設 Internet Information Services (IIS)。</span><span class="sxs-lookup"><span data-stu-id="d91b5-125">You may need to reset Internet Information Services (IIS) if the previous .dll file is still in the ASPNET worker process.</span></span>  
  
## <a name="web-service-and-web-method-attributes"></a><span data-ttu-id="d91b5-126">Web 服務和 Web 方法的屬性</span><span class="sxs-lookup"><span data-stu-id="d91b5-126">Web service and Web method attributes</span></span>  
 <span data-ttu-id="d91b5-127">[BizTalk Web 服務發佈精靈] 不允許您自訂 ASP.NET 中使用的 Web 服務或 Web 方法的屬性。</span><span class="sxs-lookup"><span data-stu-id="d91b5-127">The BizTalk Web Services Publishing Wizard does not allow you to customize the Web service or Web method attributes you use in ASP.NET.</span></span> <span data-ttu-id="d91b5-128">某些屬性會根據精靈提供的資訊自動設定。</span><span class="sxs-lookup"><span data-stu-id="d91b5-128">Some attributes are automatically set based upon information that the wizard provides.</span></span> <span data-ttu-id="d91b5-129">精靈不會使用其他屬性。</span><span class="sxs-lookup"><span data-stu-id="d91b5-129">The wizard does not use the other attributes.</span></span>  
  
 <span data-ttu-id="d91b5-130">修改現有的屬性或新增屬性至 [BizTalk Web 服務發佈精靈] 產生的 Web 服務，可能會造成 Web 服務運作不正常。</span><span class="sxs-lookup"><span data-stu-id="d91b5-130">Modifying the existing attributes or adding new attributes to Web services that the BizTalk Web Services Publishing Wizard generates may cause the Web service to function incorrectly.</span></span>  
  
 <span data-ttu-id="d91b5-131">如需有關 Web 服務和 Web 方法屬性的詳細資訊，請參閱 < **WebServiceAttribute**並**WebMethodAttribute** .NET Framework SDK 文件中的類別。</span><span class="sxs-lookup"><span data-stu-id="d91b5-131">For more information about Web services and Web method attributes, see the **WebServiceAttribute** and **WebMethodAttribute** classes in the .NET Framework SDK documentation.</span></span>  
  
## <a name="web-method-required"></a><span data-ttu-id="d91b5-132">需要 Web 方法</span><span class="sxs-lookup"><span data-stu-id="d91b5-132">Web method required</span></span>  
 <span data-ttu-id="d91b5-133">Web 服務必須至少擁有一個 Web 方法。</span><span class="sxs-lookup"><span data-stu-id="d91b5-133">A Web service must have at least one Web method.</span></span> <span data-ttu-id="d91b5-134">如果沒有 Web 方法，連接埠類型將不會建立其作業。</span><span class="sxs-lookup"><span data-stu-id="d91b5-134">Without at least one Web method, port types will not have their operations created.</span></span> <span data-ttu-id="d91b5-135">XLANG/s 不支援未包含作業的連接埠類型。</span><span class="sxs-lookup"><span data-stu-id="d91b5-135">XLANG/s does not support port types that do not have operations.</span></span>  
  
## <a name="dbcs-character-support"></a><span data-ttu-id="d91b5-136">DBCS 字元支援</span><span class="sxs-lookup"><span data-stu-id="d91b5-136">DBCS character support</span></span>  
 <span data-ttu-id="d91b5-137">Web 服務不支援中文/日文/韓文 (CJK) Unified Ideograph Extension A 等字元。</span><span class="sxs-lookup"><span data-stu-id="d91b5-137">Web services do not support Chinese/Japanese/Korean (CJK) Unified Ideograph Extension A characters.</span></span>  
  
## <a name="republishing-web-services-using-the-biztalk-web-services-publishing-wizard"></a><span data-ttu-id="d91b5-138">使用 BizTalk Web 服務發佈精靈重新發佈 Web 服務</span><span class="sxs-lookup"><span data-stu-id="d91b5-138">Republishing Web services using the BizTalk Web Services Publishing Wizard</span></span>  
 <span data-ttu-id="d91b5-139">您可以使用 [BizTalk Web 服務發佈精靈] 重新發佈已發佈的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="d91b5-139">You can use the BizTalk Web Services Publishing Wizard to republish a published Web service.</span></span> <span data-ttu-id="d91b5-140">在  **Web**<strong>服務</strong>**專案**頁面上，您可以選取**覆寫**<strong>Web</strong> **服務**選項。</span><span class="sxs-lookup"><span data-stu-id="d91b5-140">On the **Web**<strong>Service</strong>**Project** page, you can select the **Overwrite**<strong>Web</strong>**Service** option.</span></span>  
  
 <span data-ttu-id="d91b5-141">精靈不會儲存之前使用的設定。</span><span class="sxs-lookup"><span data-stu-id="d91b5-141">The wizard does not store previously used settings.</span></span> <span data-ttu-id="d91b5-142">如果您在重新執行精靈時變更設定，任何使用 (呼叫) 已發佈服務的 Web 用戶端都可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="d91b5-142">If you make changes in the settings when you rerun the wizard, any Web clients that consume (call) the published Web service may fail.</span></span> <span data-ttu-id="d91b5-143">您應該更新任何使用 (呼叫) 已發佈 Web 服務之用戶端的 Web 參考。</span><span class="sxs-lookup"><span data-stu-id="d91b5-143">You should update the Web references of any clients that consume (call) a republished Web service.</span></span>  
  
## <a name="clients-of-published-web-services-may-not-receive-server-script-timeout-errors"></a><span data-ttu-id="d91b5-144">已發佈的 Web 服務用戶端可能無法接收伺服器指令碼逾時錯誤</span><span class="sxs-lookup"><span data-stu-id="d91b5-144">Clients of published Web services may not receive Server script timeout errors</span></span>  
 <span data-ttu-id="d91b5-145">產生 Web 服務發佈精靈 中的 web 服務[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]設定預設的指令碼逾時值**110**秒。</span><span class="sxs-lookup"><span data-stu-id="d91b5-145">Web services generated with the Web Services Publishing Wizard in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] are configured by default with a script timeout value of **110** seconds.</span></span> <span data-ttu-id="d91b5-146">這是 .NET Framework 的預設值。</span><span class="sxs-lookup"><span data-stu-id="d91b5-146">This is the default value for the .NET Framework.</span></span> <span data-ttu-id="d91b5-147">**HttpServerUtility.ScriptTimeout**屬性。</span><span class="sxs-lookup"><span data-stu-id="d91b5-147">**HttpServerUtility.ScriptTimeout** property.</span></span> <span data-ttu-id="d91b5-148">使用.NET Framework 的 web 用戶端設定預設的要求逾時值**100**秒。</span><span class="sxs-lookup"><span data-stu-id="d91b5-148">Web clients that use .NET Framework are configured by default with a request timeout value of **100** seconds.</span></span> <span data-ttu-id="d91b5-149">這是.NET Framework 的預設值**HttpWebRequest.Timeout**屬性。</span><span class="sxs-lookup"><span data-stu-id="d91b5-149">This is the default value for the .NET Framework **HttpWebRequest.Timeout** property.</span></span>  
  
 <span data-ttu-id="d91b5-150">如果使用 .NET Framework 的 Web 用戶端將會呼叫以 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web 服務發佈精靈] 所產生的 Web 服務，這時因為用戶端要求逾時依預設會先行發生，所以用戶端可能就無法接收到伺服器指令碼逾時錯誤。</span><span class="sxs-lookup"><span data-stu-id="d91b5-150">If Web clients that use .NET framework are calling a Web Service generated with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web Services Publishing Wizard, it is possible that the client cannot receive server script timeout errors because the client request timeout occurs first by default.</span></span> <span data-ttu-id="d91b5-151">若要解決這個問題，您可以執行下列其中一項工作：</span><span class="sxs-lookup"><span data-stu-id="d91b5-151">To resolve this problem you can do one of the following:</span></span>  
  
-   <span data-ttu-id="d91b5-152">藉由增加的值增加到大於伺服器指令碼逾時的用戶端要求逾時**HttpWebRequest.Timeout**用戶端上的屬性。</span><span class="sxs-lookup"><span data-stu-id="d91b5-152">Increase the client request timeout to a value greater than the server script timeout by increasing the value for the **HttpWebRequest.Timeout** property on the client.</span></span>  
  
-   <span data-ttu-id="d91b5-153">藉由減少的值減少為小於用戶端要求逾時的伺服器指令碼逾時**HttpServerUtility.ScriptTimeout**伺服器上的屬性。</span><span class="sxs-lookup"><span data-stu-id="d91b5-153">Reduce the server script timeout to a value less than the client request timeout by reducing the value for the **HttpServerUtility.ScriptTimeout** property on the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d91b5-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d91b5-154">See Also</span></span>  
 [<span data-ttu-id="d91b5-155">發佈 Web 服務</span><span class="sxs-lookup"><span data-stu-id="d91b5-155">Publishing Web Services</span></span>](../core/publishing-web-services.md)