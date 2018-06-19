---
title: 從舊版的 SSO 升級 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- upgrading, SSO
- SSO, upgrading
ms.assetid: 78b99d99-9a10-4453-9db5-ae1bacd7de50
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf36c33b9480c0e8658089fdc9d996b3701d7660
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22286966"
---
# <a name="upgrading-from-a-previous-version-of-sso"></a><span data-ttu-id="55c16-102">從舊版的 SSO 升級</span><span class="sxs-lookup"><span data-stu-id="55c16-102">Upgrading from a Previous Version of SSO</span></span>
<span data-ttu-id="55c16-103">如果您要安裝 「 企業單一登入 」 功能，而且您已經在電腦上 （例如，從 Microsoft BizTalk Server 2009) 部署舊版本，您必須完成下列步驟。</span><span class="sxs-lookup"><span data-stu-id="55c16-103">If you are installing the Enterprise Single Sign-on feature and you already have a previous version deployed on your computer (for example, from Microsoft BizTalk Server 2009), you must complete the steps below.</span></span>  
  
1.  <span data-ttu-id="55c16-104">將 SSO 資料庫備份到安全位置</span><span class="sxs-lookup"><span data-stu-id="55c16-104">Back up the SSO database to a secure location</span></span>  
  
2.  <span data-ttu-id="55c16-105">將主要密碼金鑰備份至主要密碼伺服器</span><span class="sxs-lookup"><span data-stu-id="55c16-105">Back up the master secret key on the master secret server</span></span>  
  
3.  <span data-ttu-id="55c16-106">執行來更新主要密碼伺服器[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝程式，選擇**自訂安裝**，然後選取**企業單一登入**。</span><span class="sxs-lookup"><span data-stu-id="55c16-106">Update the master secret server by running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] setup, choosing **Custom Installation**, and then selecting **Enterprise Single Sign-On**.</span></span>  
  
4.  <span data-ttu-id="55c16-107">選取之後**啟用企業單一登入此電腦上**，選取**加入現有的 SSO 系統**。</span><span class="sxs-lookup"><span data-stu-id="55c16-107">After selecting **Enable Enterprise Single Sign-on on this computer**, select **Join an existing SSO system**.</span></span>  
  
 <span data-ttu-id="55c16-108">您不需要從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝來更新其他的 SSO 伺服器 (非主要密碼伺服器)。</span><span class="sxs-lookup"><span data-stu-id="55c16-108">It is not necessary to update the other SSO servers (non-master secret servers) from your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation.</span></span> <span data-ttu-id="55c16-109">但是若您希望這類伺服器提供新的「企業單一登入」功能，您就必須使用上述的相同程序來加以更新。</span><span class="sxs-lookup"><span data-stu-id="55c16-109">However, if you want the new Enterprise Single Sign-On features to be available on those servers, you must update them by using the same procedure outlined above.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55c16-110">如果您要在已安裝 Host Integration Server 2009 企業單一登入的電腦上安裝 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，且您希望更新這些伺服器，也要注意這幾項考量。</span><span class="sxs-lookup"><span data-stu-id="55c16-110">These considerations also apply if you are installing Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on a computer with an existing installation of Host Integration Server 2009 Enterprise Single Sign-On, and you want to update the servers.</span></span>  
  
 <span data-ttu-id="55c16-111">如果您要安裝 Host Integration Server 的電腦上其中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]是已安裝，請勿選取 [企業單一登入] 功能。</span><span class="sxs-lookup"><span data-stu-id="55c16-111">If you are installing Host Integration Server on a computer where [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is already installed, do not select the Enterprise Single Sign-On feature.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="55c16-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="55c16-112">In This Section</span></span>  
  
-   [<span data-ttu-id="55c16-113">使用主控件初始化的 SSO 功能</span><span class="sxs-lookup"><span data-stu-id="55c16-113">Using Host Initiated SSO Functionality</span></span>](../core/using-host-initiated-sso-functionality.md)  
  
-   [<span data-ttu-id="55c16-114">SSO 的處理伺服器</span><span class="sxs-lookup"><span data-stu-id="55c16-114">Processing Servers for SSO</span></span>](../core/processing-servers-for-sso.md)