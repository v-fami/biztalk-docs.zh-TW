---
title: "標準 SSO 安裝選項 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installing, SSO
- SSO, installing
ms.assetid: 59aeb503-f369-4145-8a3c-ab60e9ed31a8
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26441ca5d63ebdb4cba807173f7e7068ff846bdf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="standard-sso-installation-options"></a><span data-ttu-id="61ba8-102">標準 SSO 安裝選項</span><span class="sxs-lookup"><span data-stu-id="61ba8-102">Standard SSO Installation Options</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="61ba8-103"> 會利用「企業單一登入」(SSO) 功能安全地儲存認證，來啟用單一登入實例。</span><span class="sxs-lookup"><span data-stu-id="61ba8-103"> leverages the Enterprise Single Sign-On (SSO) capabilities for securely storing credentials to enable single sign-on scenarios.</span></span>  
  
 <span data-ttu-id="61ba8-104">BizTalk Server 也使用 SSO，安全地儲存配接器的自訂組態資料。</span><span class="sxs-lookup"><span data-stu-id="61ba8-104">BizTalk Server also uses SSO to store custom configuration data of Adapters securely.</span></span> <span data-ttu-id="61ba8-105">若要執行，BizTalk Server 執行階段和管理功能會將 SSO 安裝為相依的功能。</span><span class="sxs-lookup"><span data-stu-id="61ba8-105">To do this, BizTalk Server runtime and administration features install SSO as a dependent feature.</span></span> <span data-ttu-id="61ba8-106">BizTalk Server 的預設安裝會安裝「企業單一登入」。</span><span class="sxs-lookup"><span data-stu-id="61ba8-106">The default installation of BizTalk Server installs Enterprise SSO.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61ba8-107">在安裝「企業單一登入」(伺服器元件) 時，必須執行組態。</span><span class="sxs-lookup"><span data-stu-id="61ba8-107">When Enterprise Single Sign-on (Server component) is installed, configuration needs to be performed.</span></span> <span data-ttu-id="61ba8-108">設定 SSO 系統的第一個步驟是設定主要密碼伺服器。</span><span class="sxs-lookup"><span data-stu-id="61ba8-108">The first step to set up an SSO System is to configure the master secret server.</span></span> <span data-ttu-id="61ba8-109">建議您設定獨立的主要密碼伺服器。</span><span class="sxs-lookup"><span data-stu-id="61ba8-109">It is recommended to set up a stand-alone master secret server.</span></span> <span data-ttu-id="61ba8-110">僅需從 BizTalk Server 安裝的自訂功能樹狀結構中選取「企業單一登入」即可達成。</span><span class="sxs-lookup"><span data-stu-id="61ba8-110">This can be done by only selecting Enterprise Single Sign-on from the custom feature tree in BizTalk Server setup.</span></span>  
>   
>  <span data-ttu-id="61ba8-111">同時，也建議在任何執行「企業單一登入」的電腦上執行時間同步服務。</span><span class="sxs-lookup"><span data-stu-id="61ba8-111">We also recommend that any computer running Enterprise Single Sign-On have a time synchronization service running.</span></span> <span data-ttu-id="61ba8-112">如此可讓電腦時間與系統的其他部分同步，這是讓 SSO 票證服務正常運作的必要動作。</span><span class="sxs-lookup"><span data-stu-id="61ba8-112">This keeps the computer time in sync with the rest of the system, which is necessary for SSO ticketing services to function properly.</span></span>  
  
 <span data-ttu-id="61ba8-113">**安裝選項的清單**： 執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝程式。</span><span class="sxs-lookup"><span data-stu-id="61ba8-113">**List of installation options**: Run the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] setup program.</span></span> <span data-ttu-id="61ba8-114">選取**自訂安裝**，然後從下列清單中選取適當的選項：</span><span class="sxs-lookup"><span data-stu-id="61ba8-114">Select **Custom Installation**, and then select the appropriate option from the following list:</span></span>  
  
-   <span data-ttu-id="61ba8-115">**企業單一登入管理 ―**對應與連接到企業單一登入服務的系統管理和用戶端工具。</span><span class="sxs-lookup"><span data-stu-id="61ba8-115">**Enterprise Single Sign-On Administration ―** Administration and client tools for mapping and connecting to Enterprise Single Sign-On Services.</span></span>  
  
-   <span data-ttu-id="61ba8-116">**企業單一登入主要密碼伺服器 ―**做為主要密碼伺服器，SSO 系統中。</span><span class="sxs-lookup"><span data-stu-id="61ba8-116">**Enterprise Single Sign-On Master Secret Server ―** Acts as the Master Secret Server in the SSO System.</span></span> <span data-ttu-id="61ba8-117">這是 SSO 系統中必須部署的第一台伺服器，可讓您建立 SSO 資料庫。</span><span class="sxs-lookup"><span data-stu-id="61ba8-117">This is the first server in the SSO System that needs to deployed and this allows you to create the SSO database.</span></span>  
  
 <span data-ttu-id="61ba8-118">您也可以等到安裝完成後，再使用 [新增或移除程式] 工具新增下列項目：</span><span class="sxs-lookup"><span data-stu-id="61ba8-118">You can also add the following after setup, by using the Add or Remove Programs utility:</span></span>  
  
-   <span data-ttu-id="61ba8-119">**伺服器執行階段 ―**核心服務，以啟用單一登入並安全地儲存/存取組態資料。</span><span class="sxs-lookup"><span data-stu-id="61ba8-119">**Server Runtime ―** Core services to enable single sign-on and to store/access configuration data securely.</span></span>  
  
-   <span data-ttu-id="61ba8-120">**企業單一登入管理 ―**對應與連接到企業單一登入服務的系統管理和用戶端工具。</span><span class="sxs-lookup"><span data-stu-id="61ba8-120">**Enterprise Single Sign-On Administration ―** Administration and client tools for mapping and connecting to Enterprise Single Sign-On Services.</span></span>  
  
-   <span data-ttu-id="61ba8-121">**企業單一登入服務的密碼同步化 ―**服務以啟用 Enterprise SSO 系統中的密碼同步處理功能。</span><span class="sxs-lookup"><span data-stu-id="61ba8-121">**Enterprise Single Sign-On Services with Password Synchronization ―** Services to enable the Password Synchronization feature in the Enterprise SSO System.</span></span> <span data-ttu-id="61ba8-122">這些服務也和「Microsoft 密碼變更通知服務」整合。</span><span class="sxs-lookup"><span data-stu-id="61ba8-122">These services also integrate with the Microsoft Password Change Notification Service.</span></span> <span data-ttu-id="61ba8-123">安裝「企業單一登入」服務之後，您可以從 BizTalk Server 封裝啟動 \Platform\SSO\Setup.exe，然後選取「密碼同步」功能，來安裝「企業單一登入」的「密碼同步」功能。</span><span class="sxs-lookup"><span data-stu-id="61ba8-123">Once you have installed the core Enterprise Single Sign-On services, you can install the Password Synchronization feature of Enterprise SSO from the BizTalk Server package by launching the \Platform\SSO\Setup.exe and selecting the Password Synchronization feature.</span></span>  
  
-   <span data-ttu-id="61ba8-124">**軟體開發套件**程式設計及參考資訊。</span><span class="sxs-lookup"><span data-stu-id="61ba8-124">**Software Development Kit** Programming and Reference information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="61ba8-125">本節內容</span><span class="sxs-lookup"><span data-stu-id="61ba8-125">In This Section</span></span>  
  
-   [<span data-ttu-id="61ba8-126">如何安裝 SSO 管理元件</span><span class="sxs-lookup"><span data-stu-id="61ba8-126">How to Install the SSO Administration Component</span></span>](../core/how-to-install-the-sso-administration-component.md)  
  
-   [<span data-ttu-id="61ba8-127">如何安裝 SSO 用戶端公用程式</span><span class="sxs-lookup"><span data-stu-id="61ba8-127">How to Install the SSO Client Utility</span></span>](../core/how-to-install-the-sso-client-utility.md)