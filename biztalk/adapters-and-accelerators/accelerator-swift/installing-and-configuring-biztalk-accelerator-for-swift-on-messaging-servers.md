---
title: 上安裝和設定 BizTalk Accelerator for SWIFT 訊息伺服器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BizTalk Accelerator for SWIFT, configuring
- BizTalk Accelerator for SWIFT, installing on Messaging servers
- BizTalk Messaging servers, installing BizTalk Accelerator for SWIFT
ms.assetid: 7a8f60aa-5ff2-4584-9d4a-dc4a0ba61aca
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef434603c1740375f4399f368e89f99a923cba86
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22209390"
---
# <a name="installing-and-configuring-biztalk-accelerator-for-swift-on-messaging-servers"></a><span data-ttu-id="f4089-102">上安裝和設定 BizTalk Accelerator for SWIFT 訊息伺服器</span><span class="sxs-lookup"><span data-stu-id="f4089-102">Installing and Configuring BizTalk Accelerator for SWIFT on Messaging Servers</span></span>
<span data-ttu-id="f4089-103">本章節描述如何安裝及設定[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]傳訊的伺服器上。</span><span class="sxs-lookup"><span data-stu-id="f4089-103">This section describes how to install and configure [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] on the messaging servers.</span></span> <span data-ttu-id="f4089-104">這些伺服器主要用於通訊的 SWIFT 網路。</span><span class="sxs-lookup"><span data-stu-id="f4089-104">These servers are mainly used to communicate with the SWIFT Network.</span></span>  
  
### <a name="to-install-and-configure-biztalk-accelerator-for-a4swift-on-the-messaging-server"></a><span data-ttu-id="f4089-105">安裝和設定 BizTalk Accelerator for A4SWIFT 傳訊的伺服器上</span><span class="sxs-lookup"><span data-stu-id="f4089-105">To install and configure BizTalk Accelerator for A4SWIFT on the Messaging Server</span></span>  
  
1.  <span data-ttu-id="f4089-106">執行自訂安裝[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f4089-106">Perform a Custom Install of [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)].</span></span> <span data-ttu-id="f4089-107">安裝**MRSR**和**SWIFT 訊息**功能。</span><span class="sxs-lookup"><span data-stu-id="f4089-107">Install the **MRSR** and **SWIFT Messages** features.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f4089-108">您不需要安裝 Web 元件 Message Repair 和 New Submission 的功能，因為此伺服器並沒有 MRSR 站台。</span><span class="sxs-lookup"><span data-stu-id="f4089-108">You do not need to install the Web Components for Message Repair and New Submission feature because this server does not have MRSR site.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f4089-109">安裝完成後，「 組態精靈 」 會啟動。</span><span class="sxs-lookup"><span data-stu-id="f4089-109">After installation is complete, the Configuration Wizard starts.</span></span>  
  
2.  <span data-ttu-id="f4089-110">在 Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]組態主控台中，設定**MCRR**。</span><span class="sxs-lookup"><span data-stu-id="f4089-110">In the Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Configuration console, configure **MCRR**.</span></span>