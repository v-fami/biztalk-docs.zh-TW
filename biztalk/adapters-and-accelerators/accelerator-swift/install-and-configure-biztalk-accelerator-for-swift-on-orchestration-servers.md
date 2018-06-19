---
title: 安裝和設定 BizTalk Accelerator for SWIFT 協調流程伺服器上 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestration server, installing BizTalk Accelerator for SWIFT
- BizTalk Accelerator for SWIFT, installing on orchestration server
ms.assetid: 127113ae-46b4-4290-a2c1-6a3db04cd178
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 384548de9fb0b7a5ee4ce440869c42fdfa1e93ef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22209742"
---
# <a name="installing-and-configuring-biztalk-accelerator-for-swift-on-orchestration-servers"></a><span data-ttu-id="06ffd-102">安裝和設定 BizTalk Accelerator for SWIFT 協調流程伺服器上</span><span class="sxs-lookup"><span data-stu-id="06ffd-102">Installing and Configuring BizTalk Accelerator for SWIFT on Orchestration Servers</span></span>
<span data-ttu-id="06ffd-103">本章節描述如何安裝及設定[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]協調流程伺服器上。</span><span class="sxs-lookup"><span data-stu-id="06ffd-103">This section describes how to install and configure [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] on the orchestration servers.</span></span> <span data-ttu-id="06ffd-104">這些伺服器是主要用來執行 FIN 修復和重新調整協調流程和訊息修復/新增提交協調流程。</span><span class="sxs-lookup"><span data-stu-id="06ffd-104">These servers are mainly used to run the FIN Repair and Reconciliation orchestration and the Message Repair/New Submission orchestration.</span></span>  
  
### <a name="to-install-and-configure-biztalk-accelerator-for-swift-on-the-orchestration-server"></a><span data-ttu-id="06ffd-105">安裝和設定 BizTalk Accelerator for SWIFT，協調流程伺服器上</span><span class="sxs-lookup"><span data-stu-id="06ffd-105">To install and configure BizTalk Accelerator for SWIFT on the orchestration server</span></span>  
  
1.  <span data-ttu-id="06ffd-106">執行自訂安裝[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="06ffd-106">Perform a Custom Install of [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)].</span></span> <span data-ttu-id="06ffd-107">安裝**MRSR**功能。</span><span class="sxs-lookup"><span data-stu-id="06ffd-107">Install the **MRSR** feature.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="06ffd-108">您不需要安裝 Web 元件 Message Repair 和 New Submission 的功能，因為此伺服器並沒有 MRSR 站台。</span><span class="sxs-lookup"><span data-stu-id="06ffd-108">You do not need to install the Web Components for Message Repair and New Submission feature because this server does not have MRSR site.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="06ffd-109">安裝完成後，「 組態精靈 」 會啟動。</span><span class="sxs-lookup"><span data-stu-id="06ffd-109">After installation is complete, the Configuration Wizard starts.</span></span>  
  
2.  <span data-ttu-id="06ffd-110">在 Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]組態主控台中，設定**MCRR**。</span><span class="sxs-lookup"><span data-stu-id="06ffd-110">In the Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Configuration console, configure **MCRR**.</span></span>