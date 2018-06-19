---
title: Web 服務的發行時的考量 |Microsoft 文件
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
ms.openlocfilehash: 825a16555f0b0c82282ae4d85592567d2a19c073
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "22239118"
---
# <a name="considerations-when-publishing-web-services"></a><span data-ttu-id="4037f-102">發佈 Web 服務的考量</span><span class="sxs-lookup"><span data-stu-id="4037f-102">Considerations When Publishing Web Services</span></span>
<span data-ttu-id="4037f-103">이 항목은 웹 서비스를 게시하기 전에 고려해야 할 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4037f-103">This topic provides information that you should consider before you publish your Web services.</span></span>  
  
## <a name="publishing-schemas-and-the-include-element"></a><span data-ttu-id="4037f-104">스키마 게시 및 include 요소</span><span class="sxs-lookup"><span data-stu-id="4037f-104">Publishing schemas and the include element</span></span>  
 <span data-ttu-id="4037f-105">有幾個案例，其中包含結構描述位置 **包括** 項目不能發行為 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="4037f-105">There are a few scenarios where schemas that contain the **include** element cannot be published as a Web service.</span></span> <span data-ttu-id="4037f-106">오류는 BizTalk 웹 서비스 게시 마법사를 완료할 때 발생하며,</span><span class="sxs-lookup"><span data-stu-id="4037f-106">An error will occur when you complete the BizTalk Web Services Publishing Wizard.</span></span> <span data-ttu-id="4037f-107">이러한 제한에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4037f-107">These restrictions include the following:</span></span>  
  
-   <span data-ttu-id="4037f-108">包含循環 (包含結構描述具有 **包括** 項目，包括結構描述)</span><span class="sxs-lookup"><span data-stu-id="4037f-108">Circular includes (the included schema has an **include** element to the including schema)</span></span>  
  
-   <span data-ttu-id="4037f-109">無法解析 **schemaLocation** 屬性會造成錯誤</span><span class="sxs-lookup"><span data-stu-id="4037f-109">An unresolved **schemaLocation** attribute will cause an error</span></span>  
  
 <span data-ttu-id="4037f-110">如需有關的限制包含項目，請參閱 < 包含的項目繫結支援 >，網址[ http://go.microsoft.com/fwlink/?LinkId=62312 ](http://go.microsoft.com/fwlink/?LinkId=62312)。</span><span class="sxs-lookup"><span data-stu-id="4037f-110">For more information about the limitation of include element, see "Include Element Binding Support" at [http://go.microsoft.com/fwlink/?LinkId=62312](http://go.microsoft.com/fwlink/?LinkId=62312).</span></span>  
  
## <a name="publishing-schemas-and-the-import-element"></a><span data-ttu-id="4037f-111">스키마 게시 및 import 요소</span><span class="sxs-lookup"><span data-stu-id="4037f-111">Publishing schemas and the import element</span></span>  
 <span data-ttu-id="4037f-112">BizTalk 웹 서비스 게시 마법사에는 .NET Framework에 포함된 XSD.exe와 같은 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4037f-112">BizTalk Web Services Publishing Wizard has the same limitation as XSD.exe included in .NET Framework.</span></span> <span data-ttu-id="4037f-113">詳細資訊，請參閱 < 匯入項目繫結支援 >，網址[ http://go.microsoft.com/fwlink/?LinkId=62311 ](http://go.microsoft.com/fwlink/?LinkId=62311)。</span><span class="sxs-lookup"><span data-stu-id="4037f-113">For more information, see "Import Element Binding Support" at [http://go.microsoft.com/fwlink/?LinkId=62311](http://go.microsoft.com/fwlink/?LinkId=62311).</span></span>  
  
## <a name="publishing-schemas-and-the-redefine-element"></a><span data-ttu-id="4037f-114">스키마 게시 및 redefine 요소</span><span class="sxs-lookup"><span data-stu-id="4037f-114">Publishing schemas and the redefine element</span></span>  
 <span data-ttu-id="4037f-115">BizTalk 웹 서비스 게시 마법사에는 .NET Framework에 포함된 XSD.exe와 같은 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4037f-115">BizTalk Web Services Publishing Wizard has the same limitation as XSD.exe included in .NET Framework.</span></span> <span data-ttu-id="4037f-116">詳細資訊，請參閱 < Redefine 項目繫結支援 >，網址[ http://go.microsoft.com/fwlink/?LinkId=62313 ](http://go.microsoft.com/fwlink/?LinkId=62313)。</span><span class="sxs-lookup"><span data-stu-id="4037f-116">For more information, see "Redefine Element Binding Support" at [http://go.microsoft.com/fwlink/?LinkId=62313](http://go.microsoft.com/fwlink/?LinkId=62313).</span></span>  
  
## <a name="publishing-schemas-that-specify-values-for-minoccurs-or-maxoccurs-attributes"></a><span data-ttu-id="4037f-117">minOccurs 또는 maxOccurs 특성의 값을 지정하는 스키마 게시</span><span class="sxs-lookup"><span data-stu-id="4037f-117">Publishing schemas that specify values for minOccurs or maxOccurs attributes</span></span>  
 <span data-ttu-id="4037f-118">如果您要發行的結構描述包含 **minOccurs** 或 **maxOccurs** 具有特定值的屬性，這些值可能不同於已發行的 Web 服務所公開的結構描述。</span><span class="sxs-lookup"><span data-stu-id="4037f-118">If you publish a schema that contains **minOccurs** or **maxOccurs** attributes with specific values, these values may be different in schema exposed by the published Web service.</span></span> <span data-ttu-id="4037f-119">경험을 바탕으로 한 일반적 규칙으로, 모든 minOccurs 특성은 0(minOccurs=0)으로 변환되고 maxOccurs 특성은 1 또는 unbounded(maxOccurs=1 or maxOccurs=unbounded)로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4037f-119">As a general rule of thumb, all minOccurs attributes are converted to 0 (minOccurs=0) and maxOccurs attributes are converted to either 1 or unbounded (maxOccurs=1 or maxOccurs=unbounded).</span></span>  
  
## <a name="publishing-envelope-schemas"></a><span data-ttu-id="4037f-120">봉투(Envelope) 스키마 게시</span><span class="sxs-lookup"><span data-stu-id="4037f-120">Publishing envelope schemas</span></span>  
 <span data-ttu-id="4037f-121">웹 서비스로 게시 중인 봉투(Envelope) 스키마가 있으면 생성된 웹 프로젝트를 수동으로 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4037f-121">If you have an envelop schema that you are publishing as a Web service, you need to manually modify the generated Web project.</span></span>  
  
#### <a name="to-modify-the-generated-web-project-for-envelope-schemas"></a><span data-ttu-id="4037f-122">봉투(Envelope) 스키마에 대해 생성된 웹 프로젝트를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="4037f-122">To modify the generated Web project for envelope schemas</span></span>  
  
1.  <span data-ttu-id="4037f-123"><`myWebService`>.asmx.cs 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4037f-123">Open the <`myWebService`>.asmx.cs file.</span></span>  
  
2.  <span data-ttu-id="4037f-124">파일을 편집하여 `bodyTypeAssemblyQualifiedName = <dll.name.version.>`을 `bodyTypeAssemblyQualifiedName = null`로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="4037f-124">Edit the file and change `bodyTypeAssemblyQualifiedName = <dll.name.version.>` to `bodyTypeAssemblyQualifiedName = null`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4037f-125">이전 .dll이 여전히 ASPNET 작업자 프로세스에 있는 경우 IIS(인터넷 정보 서비스)를 다시 설정해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4037f-125">You may need to reset Internet Information Services (IIS) if the previous .dll file is still in the ASPNET worker process.</span></span>  
  
## <a name="web-service-and-web-method-attributes"></a><span data-ttu-id="4037f-126">웹 서비스 및 웹 메서드 특성</span><span class="sxs-lookup"><span data-stu-id="4037f-126">Web service and Web method attributes</span></span>  
 <span data-ttu-id="4037f-127">[BizTalk Web 服務發佈精靈] 不允許您自訂 ASP.NET 中使用的 Web 服務或 Web 方法的屬性。</span><span class="sxs-lookup"><span data-stu-id="4037f-127">The BizTalk Web Services Publishing Wizard does not allow you to customize the Web service or Web method attributes you use in ASP.NET.</span></span> <span data-ttu-id="4037f-128">某些屬性會根據精靈提供的資訊自動設定。</span><span class="sxs-lookup"><span data-stu-id="4037f-128">Some attributes are automatically set based upon information that the wizard provides.</span></span> <span data-ttu-id="4037f-129">나머지 특성은 마법사에서 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4037f-129">The wizard does not use the other attributes.</span></span>  
  
 <span data-ttu-id="4037f-130">기존 특성을 수정하거나 BizTalk 웹 서비스 게시 마법사가 생성하는 웹 서비스에 새 특성을 추가하면 웹 서비스가 제대로 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4037f-130">Modifying the existing attributes or adding new attributes to Web services that the BizTalk Web Services Publishing Wizard generates may cause the Web service to function incorrectly.</span></span>  
  
 <span data-ttu-id="4037f-131">如需 Web 服務和 Web 方法屬性的詳細資訊，請參閱 **WebServiceAttribute** 和 **WebMethodAttribute** 的.NET Framework SDK 文件中的類別。</span><span class="sxs-lookup"><span data-stu-id="4037f-131">For more information about Web services and Web method attributes, see the **WebServiceAttribute** and **WebMethodAttribute** classes in the .NET Framework SDK documentation.</span></span>  
  
## <a name="web-method-required"></a><span data-ttu-id="4037f-132">웹 메서드 필요</span><span class="sxs-lookup"><span data-stu-id="4037f-132">Web method required</span></span>  
 <span data-ttu-id="4037f-133">웹 서비스 하나에는 적어도 하나의 웹 메서드가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4037f-133">A Web service must have at least one Web method.</span></span> <span data-ttu-id="4037f-134">웹 메서드가 없으면 포트 유형이 작업을 만들지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="4037f-134">Without at least one Web method, port types will not have their operations created.</span></span> <span data-ttu-id="4037f-135">XLANG/s는 작업이 없는 포트 유형을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4037f-135">XLANG/s does not support port types that do not have operations.</span></span>  
  
## <a name="dbcs-character-support"></a><span data-ttu-id="4037f-136">DBCS 문자 지원</span><span class="sxs-lookup"><span data-stu-id="4037f-136">DBCS character support</span></span>  
 <span data-ttu-id="4037f-137">웹 서비스는 CJK(중국어/일본어/한국어) 통합 표의 문자 확장 A 문자를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4037f-137">Web services do not support Chinese/Japanese/Korean (CJK) Unified Ideograph Extension A characters.</span></span>  
  
## <a name="republishing-web-services-using-the-biztalk-web-services-publishing-wizard"></a><span data-ttu-id="4037f-138">BizTalk 웹 서비스 게시 마법사를 사용하여 웹 서비스 다시 게시</span><span class="sxs-lookup"><span data-stu-id="4037f-138">Republishing Web services using the BizTalk Web Services Publishing Wizard</span></span>  
 <span data-ttu-id="4037f-139">BizTalk 웹 서비스 게시 마법사를 사용하여 게시된 웹 서비스를 다시 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4037f-139">You can use the BizTalk Web Services Publishing Wizard to republish a published Web service.</span></span> <span data-ttu-id="4037f-140">在 **Web * * * Service * * * 專案**  頁面上，您可以選取 **覆寫 * * * Web * * * 服務** 選項。</span><span class="sxs-lookup"><span data-stu-id="4037f-140">On the **Web****Service****Project** page, you can select the **Overwrite****Web****Service** option.</span></span>  
  
 <span data-ttu-id="4037f-141">마법사는 이전에 사용한 설정을 저장하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4037f-141">The wizard does not store previously used settings.</span></span> <span data-ttu-id="4037f-142">마법사를 다시 실행할 때 설정을 변경하면 게시된 웹 서비스를 소비(호출)하는 웹 클라이언트에서 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4037f-142">If you make changes in the settings when you rerun the wizard, any Web clients that consume (call) the published Web service may fail.</span></span> <span data-ttu-id="4037f-143">이를 해결하려면 다시 게시된 웹 서비스를 소비(호출)하는 클라이언트의 웹 참조를 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4037f-143">You should update the Web references of any clients that consume (call) a republished Web service.</span></span>  
  
## <a name="clients-of-published-web-services-may-not-receive-server-script-timeout-errors"></a><span data-ttu-id="4037f-144">게시된 웹 서비스의 클라이언트는 서버 스크립트 시간 제한 오류를 수신하지 않음</span><span class="sxs-lookup"><span data-stu-id="4037f-144">Clients of published Web services may not receive Server script timeout errors</span></span>  
 <span data-ttu-id="4037f-145">產生的 Web 服務發佈精靈，在 web 服務[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]設定預設的指令碼逾時值**110**秒。</span><span class="sxs-lookup"><span data-stu-id="4037f-145">Web services generated with the Web Services Publishing Wizard in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] are configured by default with a script timeout value of **110** seconds.</span></span> <span data-ttu-id="4037f-146">.NET Framework의 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="4037f-146">This is the default value for the .NET Framework.</span></span> <span data-ttu-id="4037f-147">**HttpServerUtility.ScriptTimeout** 屬性。</span><span class="sxs-lookup"><span data-stu-id="4037f-147">**HttpServerUtility.ScriptTimeout** property.</span></span> <span data-ttu-id="4037f-148">使用.NET Framework 的 web 用戶端設定預設會使用要求的逾時值的 **100** 秒。</span><span class="sxs-lookup"><span data-stu-id="4037f-148">Web clients that use .NET Framework are configured by default with a request timeout value of **100** seconds.</span></span> <span data-ttu-id="4037f-149">這是.NET Framework 的預設值 **HttpWebRequest.Timeout** 屬性。</span><span class="sxs-lookup"><span data-stu-id="4037f-149">This is the default value for the .NET Framework **HttpWebRequest.Timeout** property.</span></span>  
  
 <span data-ttu-id="4037f-150">如果使用 .NET Framework 的 Web 用戶端將會呼叫以 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web 服務發佈精靈] 所產生的 Web 服務，這時因為用戶端要求逾時依預設會先行發生，所以用戶端可能就無法接收到伺服器指令碼逾時錯誤。</span><span class="sxs-lookup"><span data-stu-id="4037f-150">If Web clients that use .NET framework are calling a Web Service generated with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web Services Publishing Wizard, it is possible that the client cannot receive server script timeout errors because the client request timeout occurs first by default.</span></span> <span data-ttu-id="4037f-151">이 문제를 해결하려면 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4037f-151">To resolve this problem you can do one of the following:</span></span>  
  
-   <span data-ttu-id="4037f-152">增加用戶端要求逾時的值大於伺服器指令碼逾時的值 **HttpWebRequest.Timeout** 用戶端上的屬性。</span><span class="sxs-lookup"><span data-stu-id="4037f-152">Increase the client request timeout to a value greater than the server script timeout by increasing the value for the **HttpWebRequest.Timeout** property on the client.</span></span>  
  
-   <span data-ttu-id="4037f-153">藉由減少的值減少為小於用戶端要求逾時的伺服器指令碼逾時值 **HttpServerUtility.ScriptTimeout** 伺服器上的屬性。</span><span class="sxs-lookup"><span data-stu-id="4037f-153">Reduce the server script timeout to a value less than the client request timeout by reducing the value for the **HttpServerUtility.ScriptTimeout** property on the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4037f-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4037f-154">See Also</span></span>  
 [<span data-ttu-id="4037f-155">發佈 Web 服務</span><span class="sxs-lookup"><span data-stu-id="4037f-155">Publishing Web Services</span></span>](../core/publishing-web-services.md)