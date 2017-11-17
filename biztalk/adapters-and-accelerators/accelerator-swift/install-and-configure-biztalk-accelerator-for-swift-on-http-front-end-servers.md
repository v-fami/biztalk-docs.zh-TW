---
title: "安裝和設定 BizTalk Accelerator for SWIFT HTTP 前端伺服器上 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP server, installing BizTalk Accelerator for SWIFT
- BizTalk Accelerator for SWIFT, installing on HTTP server
ms.assetid: 1deaa5f7-9da2-4d4b-8367-2d6900065839
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe0a320f9f60f72975faf903c1355b8730840b26
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="installing-and-configuring-biztalk-accelerator-for-swift-on-http-front-end-servers"></a><span data-ttu-id="23879-102">安裝和設定 BizTalk Accelerator for SWIFT HTTP 前端伺服器上</span><span class="sxs-lookup"><span data-stu-id="23879-102">Installing and Configuring BizTalk Accelerator for SWIFT on HTTP Front-End Servers</span></span>
<span data-ttu-id="23879-103">本章節描述如何安裝及設定[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]HTTP 前端伺服器上。</span><span class="sxs-lookup"><span data-stu-id="23879-103">This section describes how to install and configure [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] on the HTTP front-end servers.</span></span> <span data-ttu-id="23879-104">這些伺服器主要用於通訊的 SWIFT 網路。</span><span class="sxs-lookup"><span data-stu-id="23879-104">These servers are mainly used to communicate with the SWIFT Network.</span></span>  
  
### <a name="to-install-and-configure-biztalk-accelerator-for-swift-on-the-http-front-end-server"></a><span data-ttu-id="23879-105">若要在安裝及設定 BizTalk Accelerator for SWIFT HTTP 前端伺服器</span><span class="sxs-lookup"><span data-stu-id="23879-105">To install and configure BizTalk Accelerator for SWIFT on the HTTP front-end server</span></span>  
  
1.  <span data-ttu-id="23879-106">執行自訂安裝[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="23879-106">Perform a Custom Install of [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)].</span></span> <span data-ttu-id="23879-107">安裝**MRSR**和**Web 元件 Message Repair 和 New Submission**功能。</span><span class="sxs-lookup"><span data-stu-id="23879-107">Install the **MRSR** and **Web Components for Message Repair and New Submission** features.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="23879-108">安裝完成後，「 組態精靈 」 會啟動。</span><span class="sxs-lookup"><span data-stu-id="23879-108">After installation is complete, the Configuration Wizard starts.</span></span>  
  
2.  <span data-ttu-id="23879-109">在 Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]組態主控台中，設定**MCRR**和**WebService**。</span><span class="sxs-lookup"><span data-stu-id="23879-109">In the Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Configuration console, configure **MCRR** and **WebService**.</span></span>  
  
3.  <span data-ttu-id="23879-110">組態精靈的 網頁伺服器上完成後，請在資料夾中開啟 web.config 檔案\<*磁碟機*>: \Program Files\Microsoft [!INCLUDE[btaA4SWIFTNoVersion](../../includes/btaa4swiftnoversion-md.md)]\Service\ [記事本] 中的。</span><span class="sxs-lookup"><span data-stu-id="23879-110">After completing the Configuration Wizard, on the Web servers, open the web.config file in the folder \<*Drive*>:\Program Files\Microsoft [!INCLUDE[btaA4SWIFTNoVersion](../../includes/btaa4swiftnoversion-md.md)]\Service\ in Notepad.</span></span> <span data-ttu-id="23879-111">搜尋 「 授權 」。</span><span class="sxs-lookup"><span data-stu-id="23879-111">Search for "Authorization".</span></span> <span data-ttu-id="23879-112">在**授權**區段中，將角色值設定為 A4SWIFT users 群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="23879-112">In the **Authorization** section, set the roles value to the name of the A4SWIFT users group.</span></span>