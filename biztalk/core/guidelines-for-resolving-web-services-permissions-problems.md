---
title: 解決 Web 服務的權限問題的指導方針 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e29543e9-9b87-437b-ac91-8f1cce01fab4
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd4420cb7c651ae1ad1bbe4bcb318b86b59c9ac4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005311"
---
# <a name="guidelines-for-resolving-web-services-permissions-problems"></a><span data-ttu-id="9c0a4-102">解決 Web 服務權限問題的指導方針</span><span class="sxs-lookup"><span data-stu-id="9c0a4-102">Guidelines for Resolving Web Services Permissions Problems</span></span>
<span data-ttu-id="9c0a4-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在使用 SOAP 配接器以及將協調流程發佈為 Web 服務時，均大量使用 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="9c0a4-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] makes extensive use of Web services for use with the SOAP adapter and when publishing orchestrations as Web services.</span></span> <span data-ttu-id="9c0a4-104">本主題包含一些一般指導方針，可用來儘可能減少 Web 服務的權限問題，另外也包含疑難排解步驟，可用於解決對 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 造成影響的 Web 服務權限的問題。</span><span class="sxs-lookup"><span data-stu-id="9c0a4-104">This topic provides some general guidelines for minimizing Web services permissions problems and steps that you can follow to troubleshoot Web services permissions problems that affect [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
## <a name="general-guidelines"></a><span data-ttu-id="9c0a4-105">一般指導方針</span><span class="sxs-lookup"><span data-stu-id="9c0a4-105">General Guidelines</span></span>  
  
- <span data-ttu-id="9c0a4-106">**設定使用者帳戶**： 確保與裝載 Web 服務的虛擬目錄相關聯的 IIS 應用程式主機處理序識別設為特定使用者帳戶，並確保此使用者帳戶會新增到下列群組：</span><span class="sxs-lookup"><span data-stu-id="9c0a4-106">**Setting user accounts**: Ensure that the IIS application host process identity associated with the virtual directory that hosts the Web service is set to a specific user account and ensure that this user account is added to the following groups:</span></span>  
  
  - <span data-ttu-id="9c0a4-107">BizTalk 外掛式主控件使用者 (網域或本機群組)</span><span class="sxs-lookup"><span data-stu-id="9c0a4-107">BizTalk Isolated Host Users (domain or local group)</span></span>  
  
  - <span data-ttu-id="9c0a4-108">IIS_WPG (本機群組)</span><span class="sxs-lookup"><span data-stu-id="9c0a4-108">IIS_WPG (local group)</span></span>  
  
    <span data-ttu-id="9c0a4-109">必須具有這 2 個群組中的成員資格，才能對 BizTalk Web 服務發佈精靈所建立的 Web 服務授與適當的權限，使其可以將 SOAP 要求訊息發佈到 BizTalk MessageBox 資料庫 (此資料庫會啟動定閱協調流程)。</span><span class="sxs-lookup"><span data-stu-id="9c0a4-109">Membership in these 2 groups is required to grant the Web service created by the BizTalk Web Service Publishing Wizard the appropriate rights to publish a SOAP request message into the BizTalk MessageBox database which will in turn activate the subscribing orchestration.</span></span> <span data-ttu-id="9c0a4-110">如需決定或設定 IIS 應用程式主機處理序識別的詳細資訊，請參閱**設定 IIS 應用程式主機處理序身分識別**一節[解決 IIS 權限問題指導方針](../core/guidelines-for-resolving-iis-permissions-problems.md).</span><span class="sxs-lookup"><span data-stu-id="9c0a4-110">For more information about determining or setting the IIS application host process identity, see the **Setting IIS Application Host Process Identity** section of [Guidelines for Resolving IIS Permissions Problems](../core/guidelines-for-resolving-iis-permissions-problems.md).</span></span>  
  
- <span data-ttu-id="9c0a4-111">**在 TEMP 環境變數所指定的資料夾上設定權限**： 請確定裝載 Web 服務的虛擬目錄的 IIS 應用程式主機處理序識別具有讀取和寫入權限所指定的資料夾TEMP 環境變數。</span><span class="sxs-lookup"><span data-stu-id="9c0a4-111">**Setting permissions on the folder specified by the TEMP environment variable**: Ensure that the IIS application host process identity for the virtual directory that hosts the Web service has read and write permissions to the folder specified by the TEMP environment variable.</span></span> <span data-ttu-id="9c0a4-112">若要決定開啟 TEMP 環境變數所指定的資料夾的命令提示字元，在 BizTalk 伺服器上，輸入下列命令，，，然後按 ENTER:</span><span class="sxs-lookup"><span data-stu-id="9c0a4-112">To determine the folder that is specified by the TEMP environment variable open a command prompt on the BizTalk Server, type the following command, and then press ENTER:</span></span>  
  
  ```  
  echo %TEMP%  
  ```  
  
   <span data-ttu-id="9c0a4-113">TEMP 環境變數所指定的資料夾，即為 Web 服務以 Just In Time (JIT) 方式編繹成動態連結程式庫 (dll) 檔案的位置，因此必須可以藉此使用者帳戶的讀寫權限來存取。</span><span class="sxs-lookup"><span data-stu-id="9c0a4-113">The folder specified by the TEMP environment variable is where the Web service is Just In Time (JIT) compiled into a dynamic link library (dll) file and therefore must be accessible with read and write permissions by this user account.</span></span>  
  
- <span data-ttu-id="9c0a4-114">**以 SOAP 方法呼叫傳送認證**： 確保 Web 服務用戶端以 SOAP 方法呼叫傳送認證。</span><span class="sxs-lookup"><span data-stu-id="9c0a4-114">**Sending credentials in the SOAP method call**: Ensure that the Web service client is sending credentials in the SOAP method call.</span></span> <span data-ttu-id="9c0a4-115">依預設在 IIS 7.0[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]需要 windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="9c0a4-115">By default IIS 7.0 in [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] requires windows authentication.</span></span> <span data-ttu-id="9c0a4-116">使用 Internet Explorer 測試 Web 服務時，會自動傳送目前已登入之使用者的認證，這就是為什麼 Web 服務可以從 Internet Explorer 使用，卻不能從其他用戶端使用的原因。</span><span class="sxs-lookup"><span data-stu-id="9c0a4-116">When testing a Web service with Internet Explorer, the credentials of the user who is currently logged on are automatically sent which is why the Web service may work from Internet Explorer but fail from another client.</span></span> <span data-ttu-id="9c0a4-117">如果 Web 服務用戶端沒有將認證加入 SOAP 方法呼叫，則會由於驗證失敗而產生 SOAP 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9c0a4-117">If the Web service client does not add credentials to the SOAP method call a SOAP exception will be generated due to an authentication failure.</span></span> <span data-ttu-id="9c0a4-118">多個如需詳細資訊傳送認證，以 SOAP 方法呼叫中提供的範例程式碼[如何使用新 System.Net 類別建立 HTTP 用戶端](http://support.microsoft.com/kb/303436)。</span><span class="sxs-lookup"><span data-stu-id="9c0a4-118">For more information about sending credentials in a SOAP method call see the sample code available in [How to use the new System.Net classes to create an HTTP client](http://support.microsoft.com/kb/303436).</span></span>  
  
- <span data-ttu-id="9c0a4-119">**針對呼叫 Web 服務的錯誤進行疑難排解**： 如果呼叫 Web 服務時，就會發生錯誤，請檢查應用程式記錄檔，或訊息透過 BizTalk Server 管理 的事件和服務執行個體追蹤**群組中樞**頁面。</span><span class="sxs-lookup"><span data-stu-id="9c0a4-119">**Troubleshooting errors calling a Web service**: If errors occur when calling a Web service, check the Application log, or message event and service instance tracking through the BizTalk Server Administration **Group Hub** page.</span></span> <span data-ttu-id="9c0a4-120">錯誤的可能原因相關資訊，請參閱[監控 BizTalk Server](../core/monitoring-biztalk-server.md)並[使用 [群組中樞] 頁面](../core/using-the-group-hub-page.md)。</span><span class="sxs-lookup"><span data-stu-id="9c0a4-120">For more information about the possible causes of the error, see [Monitoring BizTalk Server](../core/monitoring-biztalk-server.md) and [Using the Group Hub Page](../core/using-the-group-hub-page.md).</span></span>  
  
- <span data-ttu-id="9c0a4-121">**收集偵錯資訊**： 若要取得偵錯的詳細的資訊，請依照下列主題中所述的步驟[偵錯已發佈的 Web 服務](../core/debugging-published-web-services.md)如果遵循上述步驟無法解決問題。</span><span class="sxs-lookup"><span data-stu-id="9c0a4-121">**Collecting debugging information**: To obtain detailed debugging information, follow the steps outlined in the topic [Debugging Published Web Services](../core/debugging-published-web-services.md) if following the steps above does not resolve the issue.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="9c0a4-122">已知問題</span><span class="sxs-lookup"><span data-stu-id="9c0a4-122">Known Issues</span></span>  
 <span data-ttu-id="9c0a4-123">如需其他有關的已知問題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]相關的 Web 服務權限，請參閱 < You cannot call 協調流程公開為 Web 服務正在執行 BizTalk Server 的伺服器上的 「 網址[ http://go.microsoft.com/fwlink/?LinkId=196379 ](http://go.microsoft.com/fwlink/?LinkId=196379).</span><span class="sxs-lookup"><span data-stu-id="9c0a4-123">For additional information on known issues with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] related to Web services permissions, see "You cannot call an orchestration that is exposed as a Web service on a server that is running BizTalk Server" at [http://go.microsoft.com/fwlink/?LinkId=196379](http://go.microsoft.com/fwlink/?LinkId=196379).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c0a4-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c0a4-124">See Also</span></span>  
 <span data-ttu-id="9c0a4-125">[疑難排解 BizTalk Server 權限](../core/troubleshooting-biztalk-server-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="9c0a4-125">[Troubleshooting BizTalk Server Permissions](../core/troubleshooting-biztalk-server-permissions.md) </span></span>  
 [<span data-ttu-id="9c0a4-126">解決 IIS 權限問題的指導方針</span><span class="sxs-lookup"><span data-stu-id="9c0a4-126">Guidelines for Resolving IIS Permissions Problems</span></span>](../core/guidelines-for-resolving-iis-permissions-problems.md)