---
title: "如何安裝密碼同步化 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installing, Password Synchronization [SSO]
- Password Synchronization [SSO], installing
ms.assetid: 8ace0401-b759-4ea3-91a0-be2aa8b5a5a4
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ecc01ef4bc9d8bf2e82ca3dfe23b13ea0b67be2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-install-password-synchronization"></a><span data-ttu-id="a9d83-102">如何安裝密碼同步化</span><span class="sxs-lookup"><span data-stu-id="a9d83-102">How to Install Password Synchronization</span></span>
<span data-ttu-id="a9d83-103">如同其他「單一登入」功能，預設的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝中不會安裝「密碼同步」，而且必須在安裝時特別選取。</span><span class="sxs-lookup"><span data-stu-id="a9d83-103">As with the other Single Sign-On features, Password Synchronization is not installed in the default [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation, and must be specifically selected during setup.</span></span>  
  
### <a name="to-install-password-synchronization"></a><span data-ttu-id="a9d83-104">安裝密碼同步</span><span class="sxs-lookup"><span data-stu-id="a9d83-104">To install Password Synchronization</span></span>  
  
1.  <span data-ttu-id="a9d83-105">在 BizTalk Server CD 上瀏覽 **\<CDRoot > \Platforms\SSO**資料夾。</span><span class="sxs-lookup"><span data-stu-id="a9d83-105">On the BizTalk Server CD, browse to the **\<CDRoot>\Platforms\SSO** folder.</span></span>  
  
2.  <span data-ttu-id="a9d83-106">執行**setup.exe**並遵循精靈中的指示。</span><span class="sxs-lookup"><span data-stu-id="a9d83-106">Run **setup.exe** and follow the instructions in the wizard.</span></span>  
  
3.  <span data-ttu-id="a9d83-107">選取**密碼同步化**功能，並繼續進行安裝。</span><span class="sxs-lookup"><span data-stu-id="a9d83-107">Select the **Password Synchronization** feature and proceed with the installation.</span></span>  
  
 <span data-ttu-id="a9d83-108">除此之外，您還需要透過密碼同步配接器來傳送及接收外部系統的密碼變更。</span><span class="sxs-lookup"><span data-stu-id="a9d83-108">In addition to this, Password synchronization adapters are necessary to send and receive password changes to the external system.</span></span> <span data-ttu-id="a9d83-109">本節中的主題描述如何設定您自己的配接器。</span><span class="sxs-lookup"><span data-stu-id="a9d83-109">The topics in this section describe how to configure your own adapters.</span></span>  
  
 <span data-ttu-id="a9d83-110">您也可以連絡支援別名，以取得有關可用密碼同步配接器的資訊。</span><span class="sxs-lookup"><span data-stu-id="a9d83-110">You can also contact support aliases to obtain information on available Password synchronization adapters.</span></span>  
  
 <span data-ttu-id="a9d83-111">最後，若要擷取 Active Directory 中所做的密碼變更，除了安裝 ENTSSO 密碼同步功能以外，還需要在網域控制站上安裝元件來擷取密碼變更。</span><span class="sxs-lookup"><span data-stu-id="a9d83-111">Finally, to capture password changes made in Active Directory, in addition to installing the ENTSSO Password Sync feature, components need to be installed on the domain controllers to capture password changes.</span></span>  
  
 <span data-ttu-id="a9d83-112">在將要從中擷取密碼的所有網域控制器上，必須安裝 Windows 密碼擷取元件和密碼變更通知服務 (PCNS，Password Change Notification Service)。</span><span class="sxs-lookup"><span data-stu-id="a9d83-112">Both the Windows Password Capture component and Password Change Notification Service (PCNS) must be installed on all domain controllers from which you will be capturing passwords.</span></span> <span data-ttu-id="a9d83-113">您可從下列位置安裝這些元件：</span><span class="sxs-lookup"><span data-stu-id="a9d83-113">You can install these components from the following location:</span></span>  
  
 [<span data-ttu-id="a9d83-114">http://go.microsoft.com/fwlink/?LinkId=68145</span><span class="sxs-lookup"><span data-stu-id="a9d83-114">http://go.microsoft.com/fwlink/?LinkId=68145</span></span>](http://go.microsoft.com/fwlink/?LinkId=68145)  
  
 <span data-ttu-id="a9d83-115">在網域控制站上繼續執行安裝之前，請先詳閱隨附文件 (也在此資料夾中)。</span><span class="sxs-lookup"><span data-stu-id="a9d83-115">Read the accompanying documentation (also located in this folder) before you proceed with the installation on the domain controller.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9d83-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9d83-116">See Also</span></span>  
 [<span data-ttu-id="a9d83-117">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="a9d83-117">Password Synchronization</span></span>](../core/password-synchronization2.md)