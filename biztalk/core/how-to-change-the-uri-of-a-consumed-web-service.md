---
title: 如何變更已使用的 Web 服務的 URI |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Web services, modifying
- Web services, consuming
- consuming [Web services]
- modifying, Web services
ms.assetid: 907de565-8c99-4d34-939f-fd3dba37dd11
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b9ae7d7178fc24c5f16b28325fb627045e5273a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247398"
---
# <a name="how-to-change-the-uri-of-a-consumed-web-service"></a><span data-ttu-id="00cc1-102">如何變更已使用的 Web 服務的 URI</span><span class="sxs-lookup"><span data-stu-id="00cc1-102">How to Change the URI of a Consumed Web Service</span></span>
<span data-ttu-id="00cc1-103">部署協調流程後，BizTalk Server 會為協調流程參考的每個 Web 服務設定傳送埠。</span><span class="sxs-lookup"><span data-stu-id="00cc1-103">After you deploy your orchestration, BizTalk Server configures a send port for each Web service that the orchestration references.</span></span> <span data-ttu-id="00cc1-104">依照預設，BizTalk 在執行階段使用的 Web 服務 URL，和匯入的 Web 服務 URL 相同。</span><span class="sxs-lookup"><span data-stu-id="00cc1-104">By default, BizTalk uses the URL of the Web service at run time for the same URL for the imported Web service.</span></span> <span data-ttu-id="00cc1-105">您可以使用 BizTalk Server 管理主控台來變更此 URL。</span><span class="sxs-lookup"><span data-stu-id="00cc1-105">You can change this URL using BizTalk Server Administration console.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="00cc1-106">您必須先部署協調流程，才能變更已使用的 Web 服務的 URI。</span><span class="sxs-lookup"><span data-stu-id="00cc1-106">You must deploy your orchestration before you change the URI of a consumed Web service.</span></span> <span data-ttu-id="00cc1-107">如需有關如何部署您的協調流程的詳細資訊，請參閱[從到 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="00cc1-107">For more information on deploying your orchestration, see [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).</span></span>  
  
### <a name="to-change-the-uri-of-a-consumed-web-service-using-biztalk-server-administration-console"></a><span data-ttu-id="00cc1-108">若要使用 BizTalk Server 管理主控台變更已使用的 Web 服務的 URI</span><span class="sxs-lookup"><span data-stu-id="00cc1-108">To change the URI of a consumed Web service using BizTalk Server Administration Console</span></span>  
  
1.  <span data-ttu-id="00cc1-109">在 BizTalk Server 管理主控台中，展開 BizTalk 應用程式，然後展開**傳送埠**節點。</span><span class="sxs-lookup"><span data-stu-id="00cc1-109">In BizTalk Server Administration console, expand a BizTalk application, and then expand the **Send Ports** node.</span></span>  
  
2.  <span data-ttu-id="00cc1-110">以滑鼠右鍵按一下 設定與 SOAP 配接器的傳送埠，請按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="00cc1-110">Right-click a send port configured with SOAP adapter, click **Properties**.</span></span>  
  
3.  <span data-ttu-id="00cc1-111">若您沒有實體連接埠，可以使用 [BizTalk 管理主控台] 建立傳送埠和接收位置。</span><span class="sxs-lookup"><span data-stu-id="00cc1-111">If you do not have physical ports, you can create send ports and receive locations by using BizTalk Administration console.</span></span> <span data-ttu-id="00cc1-112">如需資訊，請參閱[如何建立傳送埠](../core/how-to-create-a-send-port2.md)。</span><span class="sxs-lookup"><span data-stu-id="00cc1-112">For information, see [How to Create a Send Port](../core/how-to-create-a-send-port2.md).</span></span>  
  
4.  <span data-ttu-id="00cc1-113">在**傳送屬性**對話方塊中，按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="00cc1-113">On the **Send Properties** dialog box, click **Configure**.</span></span>  
  
5.  <span data-ttu-id="00cc1-114">在**SOAP 傳輸屬性**對話方塊中，於**Web 服務 URL**方塊中，輸入 Web 服務中的位置的完整 URL，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="00cc1-114">In the **SOAP Transport Properties** dialog box, in the **Web Service URL** box, type the full URL for the location of the Web service, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="00cc1-115">請確定您指定的 URL 是否有 Web 服務存在。</span><span class="sxs-lookup"><span data-stu-id="00cc1-115">You should ensure that a Web service exists for the URL that you specify.</span></span> <span data-ttu-id="00cc1-116">BizTalk Server 不會驗證 URL 位置。</span><span class="sxs-lookup"><span data-stu-id="00cc1-116">BizTalk Server does not validate the URL location.</span></span>  
  
6.  <span data-ttu-id="00cc1-117">按一下 確定 以結束**傳送屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="00cc1-117">Click OK to exit the **Send Properties** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00cc1-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00cc1-118">See Also</span></span>  
 <span data-ttu-id="00cc1-119">[使用 BizTalk Server 管理主控台](../core/using-the-biztalk-server-administration-console.md) </span><span class="sxs-lookup"><span data-stu-id="00cc1-119">[Using the BizTalk Server Administration Console](../core/using-the-biztalk-server-administration-console.md) </span></span>  
 <span data-ttu-id="00cc1-120">[如何設定 SOAP 傳送埠](../core/how-to-configure-a-soap-send-port.md) </span><span class="sxs-lookup"><span data-stu-id="00cc1-120">[How to Configure a SOAP Send Port](../core/how-to-configure-a-soap-send-port.md) </span></span>  
 <span data-ttu-id="00cc1-121">[SOAP 標頭與已使用的 Web 服務](../core/soap-headers-with-consumed-web-services.md) </span><span class="sxs-lookup"><span data-stu-id="00cc1-121">[SOAP Headers with Consumed Web Services](../core/soap-headers-with-consumed-web-services.md) </span></span>  
 [<span data-ttu-id="00cc1-122">建立 Web 連接埠</span><span class="sxs-lookup"><span data-stu-id="00cc1-122">Creating Web Ports</span></span>](../core/creating-web-ports.md)