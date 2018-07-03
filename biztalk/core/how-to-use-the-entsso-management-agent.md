---
title: 如何使用 ENTSSO 管理代理程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c89b494-db12-4d2a-a030-6acd34489cab
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 68c354f2250e9abc6a02ea52f4b7c106f57144e6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018474"
---
# <a name="how-to-use-the-entsso-management-agent"></a><span data-ttu-id="22473-102">如何使用 ENTSSO 管理代理程式</span><span class="sxs-lookup"><span data-stu-id="22473-102">How to Use the ENTSSO Management Agent</span></span>
<span data-ttu-id="22473-103">此版本的企業單一登入 (SSO) 包含 Microsoft Identity Integration Server (MIIS) 的管理代理程式 (MA)，整合了企業單一登入與 MIIS 的帳戶同步處理功能。</span><span class="sxs-lookup"><span data-stu-id="22473-103">This version of Enterprise Single Sign-On (SSO) contains a Management Agent (MA) for Microsoft Identity Integration Server (MIIS), which integrates Enterprise SSO with the account synchronization capabilities of MIIS.</span></span> <span data-ttu-id="22473-104">這樣一來 MIIS 系統管理員即可管理 SSO 資料庫內的 SSO 對應。</span><span class="sxs-lookup"><span data-stu-id="22473-104">This enables an MIIS administrator to manage SSO mappings in the SSO Database.</span></span>  
  
 <span data-ttu-id="22473-105">在 企業單一登入，Windows 網域帳戶之間建立對應 (*domainname\username*) 和外部認證。</span><span class="sxs-lookup"><span data-stu-id="22473-105">In Enterprise SSO, mappings are created between Windows Domain accounts (*domainname\username*) and external credentials.</span></span> <span data-ttu-id="22473-106">如果您有 Active Directory 管理代理程式，並管理代理程式的外部資料來源 (範例： RACF MA)，您可以使用企業單一登入 (ENTSSO MA) 管理 SSO 資料庫中的對應。</span><span class="sxs-lookup"><span data-stu-id="22473-106">If you have an Active Directory Management Agent, and the Management Agent for the external Data Source (example: RACF MA), you can use the Enterprise SSO MA (ENTSSO MA) to manage mappings in the SSO Database.</span></span> <span data-ttu-id="22473-107">ENTSSO MA 是*呼叫為基礎的匯出*只管理代理程式。</span><span class="sxs-lookup"><span data-stu-id="22473-107">ENTSSO MA is a *Call-Based Export* Management Agent only.</span></span>  
  
 <span data-ttu-id="22473-108">設定管理代理程式可分三部分：</span><span class="sxs-lookup"><span data-stu-id="22473-108">You configure the Management Agent in three separate parts:</span></span>  
  
- <span data-ttu-id="22473-109">組態檔 (ENTSSO.xml)</span><span class="sxs-lookup"><span data-stu-id="22473-109">A configuration file (ENTSSO.xml)</span></span>  
  
- <span data-ttu-id="22473-110">MIIS 使用者介面</span><span class="sxs-lookup"><span data-stu-id="22473-110">The MIIS user interface</span></span>  
  
- <span data-ttu-id="22473-111">ENTSSO 使用者介面</span><span class="sxs-lookup"><span data-stu-id="22473-111">The ENTSSO user interface</span></span>  
  
  <span data-ttu-id="22473-112">此章節的主題會說明該組態程序。</span><span class="sxs-lookup"><span data-stu-id="22473-112">The topics in this section describe the configuration process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="22473-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="22473-113">In This Section</span></span>  
  
-   [<span data-ttu-id="22473-114">設定 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="22473-114">Configuring the XML File</span></span>](../core/configuring-the-xml-file.md)  
  
-   [<span data-ttu-id="22473-115">如何設定 ENTSSO MA 的 MIIS</span><span class="sxs-lookup"><span data-stu-id="22473-115">How to Configure MIIS for ENTSSO MA</span></span>](../core/how-to-configure-miis-for-entsso-ma.md)  
  
-   [<span data-ttu-id="22473-116">如何設定 ENTSSO 以進行 MIIS 密碼同步</span><span class="sxs-lookup"><span data-stu-id="22473-116">How to Configure ENTSSO for MIIS Password Sync</span></span>](../core/how-to-configure-entsso-for-miis-password-sync.md)