---
title: 加入 Web 參考 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BPEL, orchestrations
- orchestrations, BPEL
- Web services, ports
- orchestrations, exporting
- Web services, projects
- Web services, references
- projects, Web services
ms.assetid: 7e40f215-f11a-4151-bcc6-e107bf36b6f6
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2cbf8cd4c21009190fc459312467656410dc663a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25964764"
---
# <a name="adding-web-references"></a><span data-ttu-id="8b463-102">加入 Web 參考</span><span class="sxs-lookup"><span data-stu-id="8b463-102">Adding Web References</span></span>
<span data-ttu-id="8b463-103">在您加入 Web 連接埠之前，必須先將 Web 參考加入至 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="8b463-103">Before you can add a Web port, you need to add a Web reference to your BizTalk project.</span></span> <span data-ttu-id="8b463-104">Web 參考是可供專案使用的 Web 服務描述。</span><span class="sxs-lookup"><span data-stu-id="8b463-104">A Web reference is a description of a Web service that is available to your project.</span></span> <span data-ttu-id="8b463-105">當您新增 Web 參考加入您的專案時，BizTalk 專案建立協調流程 Web 連接埠類型、 Web 訊息類型、 Reference.map （對應檔案）、 Reference.odx （協調流程檔案）、 \< *WebService*\>。disco （探索檔案） 和\< *WebService*\>.wsdl （Web 服務描述語言檔案） 至您的專案。</span><span class="sxs-lookup"><span data-stu-id="8b463-105">When you add a Web reference to your project, BizTalk project creates an orchestration Web port type, Web message types, Reference.map (map file), Reference.odx (orchestration file), \<*WebService*\>.disco (discovery file), and \<*WebService*\>.wsdl (Web Service Description Language file) to your project.</span></span> <span data-ttu-id="8b463-106">如果您的「Web 服務描述語言」(WSDL) 檔案包含結構描述 Web 訊息類型，BizTalk 專案還會將 Reference.xsd 加入至您的專案。</span><span class="sxs-lookup"><span data-stu-id="8b463-106">If your Web Service Description Language (WSDL) file contains schema Web message types, BizTalk project adds Reference.xsd to your project.</span></span>  
  
 <span data-ttu-id="8b463-107">Web 參考包括：</span><span class="sxs-lookup"><span data-stu-id="8b463-107">A Web reference includes:</span></span>  
  
-   <span data-ttu-id="8b463-108">Web 服務的「統一資源定位器」(URL)。</span><span class="sxs-lookup"><span data-stu-id="8b463-108">A Universal Resource Locator (URL) for the Web service.</span></span>  
  
-   <span data-ttu-id="8b463-109">WSDL 檔案，它可提供關於服務的資訊，例如可用的方法、連接埠以及訊息類型。</span><span class="sxs-lookup"><span data-stu-id="8b463-109">A WSDL file that offers information about the service such as available methods, ports, and message types.</span></span>  
  
-   <span data-ttu-id="8b463-110">參考對應 (Reference.map)。</span><span class="sxs-lookup"><span data-stu-id="8b463-110">A reference map (Reference.map).</span></span>  
  
 <span data-ttu-id="8b463-111">加入 Web 參考時，該 Web 服務的所有 Web 方法都必須與 BizTalk Server 相容。</span><span class="sxs-lookup"><span data-stu-id="8b463-111">When you add a Web reference, all the Web methods for that Web service must be compatible with BizTalk Server.</span></span> <span data-ttu-id="8b463-112">您不能指定 Web 服務中特定 Web 方法的條件式屬性。</span><span class="sxs-lookup"><span data-stu-id="8b463-112">You cannot specify conditional attributes for specific Web methods in a Web service.</span></span>  
  
 <span data-ttu-id="8b463-113">您可以加入 Web 參考加入您的專案使用**加入 Web 參考** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8b463-113">You add a Web reference to your project by using the **Add Web Reference** dialog box.</span></span> <span data-ttu-id="8b463-114">如需新增 Web 參考的詳細資訊，請參閱[使用 Visual Studio](../core/using-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="8b463-114">For more information about adding Web references, see [Using Visual Studio](../core/using-visual-studio.md).</span></span>  
  
 <span data-ttu-id="8b463-115">如果想使用「商務程序執行語言」(Business Process Execution Language，BPEL) 匯出程序匯出您的協調流程，您不能參考現有 BizTalk 專案中的 Web 參考。</span><span class="sxs-lookup"><span data-stu-id="8b463-115">If you are planning to export your orchestration using the Business Process Execution Language (BPEL) export process, you cannot reference a Web reference from an existing BizTalk project.</span></span> <span data-ttu-id="8b463-116">如果您參考現有 BizTalk 專案中的 Web 參考，則 BPEL 匯出程序會自動產生第二個 WSDL 檔案，而您則會失去您的繫結資訊。</span><span class="sxs-lookup"><span data-stu-id="8b463-116">When you reference a Web reference from an existing BizTalk project, the BPEL export process will auto-generate a second WSDL file and you will lose your binding information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b463-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="8b463-117">See Also</span></span>  
 <span data-ttu-id="8b463-118">[建立 Web 連接埠](../core/creating-web-ports.md) </span><span class="sxs-lookup"><span data-stu-id="8b463-118">[Creating Web Ports](../core/creating-web-ports.md) </span></span>  
 [<span data-ttu-id="8b463-119">使用 Web 服務</span><span class="sxs-lookup"><span data-stu-id="8b463-119">Consuming Web Services</span></span>](../core/consuming-web-services.md)