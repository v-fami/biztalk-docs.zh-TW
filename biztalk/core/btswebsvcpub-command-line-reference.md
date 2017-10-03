---
title: "BTSWebSvcPub 命令列參照 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e19dd4d-9f2c-4a17-9437-8701e1c274fb
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c9993092c0d798ae2d47f614a24da21c3a2df62
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="btswebsvcpub-command-line-reference"></a><span data-ttu-id="c84ed-102">BTSWebSvcPub 命令列參照</span><span class="sxs-lookup"><span data-stu-id="c84ed-102">BTSWebSvcPub Command-Line Reference</span></span>
<span data-ttu-id="c84ed-103">本主題提供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所附 BTSWebSvcPub 命令列工具的參考資訊。</span><span class="sxs-lookup"><span data-stu-id="c84ed-103">This topic provides reference information for the BTSWebSvcPub command-line tool included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="c84ed-104">您可以使用 BTSWebSvcPub 建立 Web 服務 (.asmx) 以便透過該 Web 服務發佈協調流程，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c84ed-104">You can use BTSWebSvcPub to create Web services (.asmx) for publishing orchestrations through Web services as follows:</span></span>  
  
## <a name="usage"></a><span data-ttu-id="c84ed-105">使用方式</span><span class="sxs-lookup"><span data-stu-id="c84ed-105">Usage</span></span>  
 <span data-ttu-id="c84ed-106">**BTSWebSvcPub 路徑名稱 [-位置：** *值* **] [-覆寫] [-匿名]**</span><span class="sxs-lookup"><span data-stu-id="c84ed-106">**BTSWebSvcPub PathName [-Location:** *value* **] [-Overwrite] [-Anonymous]**</span></span>  
  
 <span data-ttu-id="c84ed-107">**[-Name:** *值* **] [-命名空間：** *值* **] [-TargetNamespace:** *值* **]**</span><span class="sxs-lookup"><span data-stu-id="c84ed-107">**[-Name:** *value* **] [-Namespace:** *value* **] [-TargetNamespace:** *value* **]**</span></span>  
  
 <span data-ttu-id="c84ed-108">**[-UnknownHeaders [**  *+*  **&#124;** *-*  **]] [-單一登入 [**  *+*  **&#124;** *-*  **]] [-ParameterStyle:** *值* **]**</span><span class="sxs-lookup"><span data-stu-id="c84ed-108">**[-UnknownHeaders[** *+* **&#124;** *-* **]] [-SingleSignOn[** *+* **&#124;** *-* **]] [-ParameterStyle:** *value* **]**</span></span>  
  
 <span data-ttu-id="c84ed-109">**[-下列：** *值* **] [-ForceRequestResponse:** *值* **] [-ReceiveLocation]**</span><span class="sxs-lookup"><span data-stu-id="c84ed-109">**[-ConformanceClaims:** *value* **] [-ForceRequestResponse:** *value* **] [-ReceiveLocation]**</span></span>  
  
 <span data-ttu-id="c84ed-110">**[-ApplicationName:** *值* **]**</span><span class="sxs-lookup"><span data-stu-id="c84ed-110">**[-ApplicationName:** *value* **]**</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="c84ed-111">參數</span><span class="sxs-lookup"><span data-stu-id="c84ed-111">Parameters</span></span>  
  
|<span data-ttu-id="c84ed-112">參數</span><span class="sxs-lookup"><span data-stu-id="c84ed-112">Parameter</span></span>|<span data-ttu-id="c84ed-113">Required</span><span class="sxs-lookup"><span data-stu-id="c84ed-113">Required</span></span>|<span data-ttu-id="c84ed-114">Description</span><span class="sxs-lookup"><span data-stu-id="c84ed-114">Description</span></span>|  
|---------------|--------------|-----------------|  
|<span data-ttu-id="c84ed-115">**PathName**</span><span class="sxs-lookup"><span data-stu-id="c84ed-115">**PathName**</span></span>|<span data-ttu-id="c84ed-116">是</span><span class="sxs-lookup"><span data-stu-id="c84ed-116">Yes</span></span>|<span data-ttu-id="c84ed-117">BizTalk 組件 (*.dll) 或 web 服務描述的路徑和檔案名稱 (\*.xml) 檔案。</span><span class="sxs-lookup"><span data-stu-id="c84ed-117">Path and file name of BizTalk assembly (*.dll) or web service description (\*.xml) file.</span></span>|  
|<span data-ttu-id="c84ed-118">**位置**</span><span class="sxs-lookup"><span data-stu-id="c84ed-118">**-Location**</span></span>|<span data-ttu-id="c84ed-119">否</span><span class="sxs-lookup"><span data-stu-id="c84ed-119">No</span></span>|<span data-ttu-id="c84ed-120">要發佈的位置。</span><span class="sxs-lookup"><span data-stu-id="c84ed-120">Location in which to publish.</span></span> <span data-ttu-id="c84ed-121">(語法："http://host[:port]/path")</span><span class="sxs-lookup"><span data-stu-id="c84ed-121">(Syntax:"http://host[:port]/path")</span></span>|  
|<span data-ttu-id="c84ed-122">**-覆寫**</span><span class="sxs-lookup"><span data-stu-id="c84ed-122">**-Overwrite**</span></span>|<span data-ttu-id="c84ed-123">否</span><span class="sxs-lookup"><span data-stu-id="c84ed-123">No</span></span>|<span data-ttu-id="c84ed-124">覆寫指定的位置。</span><span class="sxs-lookup"><span data-stu-id="c84ed-124">Overwrite specified location.</span></span>|  
|<span data-ttu-id="c84ed-125">**匿名**</span><span class="sxs-lookup"><span data-stu-id="c84ed-125">**-Anonymous**</span></span>|<span data-ttu-id="c84ed-126">否</span><span class="sxs-lookup"><span data-stu-id="c84ed-126">No</span></span>|<span data-ttu-id="c84ed-127">允許匿名存取 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="c84ed-127">Allow anonymous access to Web service.</span></span>|  
|<span data-ttu-id="c84ed-128">**-名稱**</span><span class="sxs-lookup"><span data-stu-id="c84ed-128">**-Name**</span></span>|<span data-ttu-id="c84ed-129">否</span><span class="sxs-lookup"><span data-stu-id="c84ed-129">No</span></span>|<span data-ttu-id="c84ed-130">要包含 Web 服務的解決方案和組件的名稱 (.sln 和 .dll 檔案)。</span><span class="sxs-lookup"><span data-stu-id="c84ed-130">Name of the solution and assembly (.sln and .dll files) that will contain the Web service.</span></span>|  
|<span data-ttu-id="c84ed-131">**命名空間**</span><span class="sxs-lookup"><span data-stu-id="c84ed-131">**-Namespace**</span></span>|<span data-ttu-id="c84ed-132">否</span><span class="sxs-lookup"><span data-stu-id="c84ed-132">No</span></span>|<span data-ttu-id="c84ed-133">Web 服務代碼的預設命名空間。</span><span class="sxs-lookup"><span data-stu-id="c84ed-133">Default namespace for Web service code.</span></span>|  
|<span data-ttu-id="c84ed-134">**-Targetnamespace**</span><span class="sxs-lookup"><span data-stu-id="c84ed-134">**-Targetnamespace**</span></span>|<span data-ttu-id="c84ed-135">否</span><span class="sxs-lookup"><span data-stu-id="c84ed-135">No</span></span>|<span data-ttu-id="c84ed-136">Web 服務的目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="c84ed-136">Target namespace of the Web service.</span></span> <span data-ttu-id="c84ed-137">(範例：'http://www.northwindtraders.com')</span><span class="sxs-lookup"><span data-stu-id="c84ed-137">(Example:'http://www.northwindtraders.com')</span></span>|  
|<span data-ttu-id="c84ed-138">**-UnknownHeaders**</span><span class="sxs-lookup"><span data-stu-id="c84ed-138">**-UnknownHeaders**</span></span>|<span data-ttu-id="c84ed-139">否</span><span class="sxs-lookup"><span data-stu-id="c84ed-139">No</span></span>|<span data-ttu-id="c84ed-140">支援未知 SOAP 標頭。</span><span class="sxs-lookup"><span data-stu-id="c84ed-140">Support unknown SOAP headers.</span></span>|  
|<span data-ttu-id="c84ed-141">**-SinglesSignon**</span><span class="sxs-lookup"><span data-stu-id="c84ed-141">**-SinglesSignon**</span></span>|<span data-ttu-id="c84ed-142">否</span><span class="sxs-lookup"><span data-stu-id="c84ed-142">No</span></span>|<span data-ttu-id="c84ed-143">支援 SharePoint Portal Server 單一登入 SOAP 標頭。</span><span class="sxs-lookup"><span data-stu-id="c84ed-143">Support SharePoint Portal Server Single Sign-On SOAP headers.</span></span>|  
|<span data-ttu-id="c84ed-144">**-ParameterStyle**</span><span class="sxs-lookup"><span data-stu-id="c84ed-144">**-ParameterStyle**</span></span>|<span data-ttu-id="c84ed-145">否</span><span class="sxs-lookup"><span data-stu-id="c84ed-145">No</span></span>|<span data-ttu-id="c84ed-146">訊息的 SoapParameterStyle:"Default"、"Bare"或"Wrapped"。</span><span class="sxs-lookup"><span data-stu-id="c84ed-146">The SoapParameterStyle for messages: "Default", "Bare",or "Wrapped".</span></span>|  
|<span data-ttu-id="c84ed-147">**-ConfirmanceClaims**</span><span class="sxs-lookup"><span data-stu-id="c84ed-147">**-ConfirmanceClaims**</span></span>|<span data-ttu-id="c84ed-148">否</span><span class="sxs-lookup"><span data-stu-id="c84ed-148">No</span></span>|<span data-ttu-id="c84ed-149">Web 服務互通性 (WSI) 主張:"None"或"BasicProfile1_1"。</span><span class="sxs-lookup"><span data-stu-id="c84ed-149">Web services interoperability (WSI) claim: "None" or"BasicProfile1_1".</span></span>|  
|<span data-ttu-id="c84ed-150">**-ForceRequestResponse**</span><span class="sxs-lookup"><span data-stu-id="c84ed-150">**-ForceRequestResponse**</span></span>|<span data-ttu-id="c84ed-151">否</span><span class="sxs-lookup"><span data-stu-id="c84ed-151">No</span></span>|<span data-ttu-id="c84ed-152">公開單向 BizTalk 作業，做為要求-回應的 Web 方法。</span><span class="sxs-lookup"><span data-stu-id="c84ed-152">Expose one-way BizTalk operations as request-response web methods.</span></span>|  
|<span data-ttu-id="c84ed-153">**-描述**</span><span class="sxs-lookup"><span data-stu-id="c84ed-153">**-ReceiveLocation**</span></span>|<span data-ttu-id="c84ed-154">否</span><span class="sxs-lookup"><span data-stu-id="c84ed-154">No</span></span>|<span data-ttu-id="c84ed-155">在指定的 BizTalk 應用程式中建立接收位置。</span><span class="sxs-lookup"><span data-stu-id="c84ed-155">Create receive locations in the specified BizTalk application.</span></span>|  
|<span data-ttu-id="c84ed-156">**-應用程式名稱**</span><span class="sxs-lookup"><span data-stu-id="c84ed-156">**-ApplicationName**</span></span>|<span data-ttu-id="c84ed-157">否</span><span class="sxs-lookup"><span data-stu-id="c84ed-157">No</span></span>|<span data-ttu-id="c84ed-158">要建立接收位置的 BizTalk 應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="c84ed-158">Name of the BizTalk application in which to create receive locations.</span></span> <span data-ttu-id="c84ed-159">若未指定，將使用預設的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c84ed-159">If not specified, the default BizTalk application is used.</span></span>|  
  
## <a name="sample"></a><span data-ttu-id="c84ed-160">範例</span><span class="sxs-lookup"><span data-stu-id="c84ed-160">Sample</span></span>  
 <span data-ttu-id="c84ed-161">BTSWebSvcPub.exe "MyAssembly.dll" -Location:http://localhost/MyVdir</span><span class="sxs-lookup"><span data-stu-id="c84ed-161">BTSWebSvcPub.exe "MyAssembly.dll" -Location:http://localhost/MyVdir</span></span>  
  
 <span data-ttu-id="c84ed-162">-Overwrite</span><span class="sxs-lookup"><span data-stu-id="c84ed-162">-Overwrite</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c84ed-163">備註</span><span class="sxs-lookup"><span data-stu-id="c84ed-163">Remarks</span></span>  
 <span data-ttu-id="c84ed-164">參數名稱不區分大小寫，而且可以縮寫。</span><span class="sxs-lookup"><span data-stu-id="c84ed-164">Parameter names are not case sensitive and may be abbreviated.</span></span> <span data-ttu-id="c84ed-165">參數值會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="c84ed-165">Parameter values are case sensitive.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c84ed-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c84ed-166">See Also</span></span>  
 [<span data-ttu-id="c84ed-167">如何使用 BizTalk Web 服務發佈精靈發佈為 Web 服務的協調流程</span><span class="sxs-lookup"><span data-stu-id="c84ed-167">How to Use the BizTalk Web Services Publishing Wizard to Publish an Orchestration as a Web Service</span></span>](../core/publish-orchestration-as-web-service--biztalk-web-services-publishing-wizard.md)