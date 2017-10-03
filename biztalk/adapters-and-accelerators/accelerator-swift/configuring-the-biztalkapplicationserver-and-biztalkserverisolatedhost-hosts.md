---
title: "設定 BizTalkApplicationServer 與 BizTalkServerIsolatedHost 主控件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, hosts
- BizTalkApplicationServer host
- hosts
- BizTalkServerIsolatedHost host
ms.assetid: 17bc9f01-ff87-427d-8411-6a065814ba1e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8459debcd52ce990bc98adf3a2a2372206bae336
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-the-biztalkapplicationserver-and-biztalkserverisolatedhost-hosts"></a><span data-ttu-id="8654d-102">設定 BizTalkApplicationServer 與 BizTalkServerIsolatedHost 主控件</span><span class="sxs-lookup"><span data-stu-id="8654d-102">Configuring the BizTalkApplicationServer and BizTalkServerIsolatedHost Hosts</span></span>
<span data-ttu-id="8654d-103">若要限制的訊息 （傳送和接收訊息） 到 BizTalk 傳訊的伺服器，您需要設定預設的主控件，哪些執行 MSMQT 傳送及接收處理常式，只在訊息的伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="8654d-103">To limit the messaging (sending and receiving messages) to the BizTalk Messaging servers, you need to configure the default hosts, which are running the MSMQT send and receive handlers, to run only on the messaging servers.</span></span>  
  
### <a name="to-configure-the-default-hosts"></a><span data-ttu-id="8654d-104">若要設定預設的主控件</span><span class="sxs-lookup"><span data-stu-id="8654d-104">To configure the default hosts</span></span>  
  
1.  <span data-ttu-id="8654d-105">使用 BizTalk 管理主控台，從 BizTalkApplicationServer 主機刪除協調流程伺服器主控件執行個體：</span><span class="sxs-lookup"><span data-stu-id="8654d-105">Using the BizTalk Administration Console, delete the orchestration servers host instances from the BizTalkApplicationServer host:</span></span>  
  
    -   <span data-ttu-id="8654d-106">以滑鼠右鍵按一下每個主控件執行個體，然後按一下**停止**。</span><span class="sxs-lookup"><span data-stu-id="8654d-106">Right-click each host instance and click **Stop**.</span></span>  
  
    -   <span data-ttu-id="8654d-107">以滑鼠右鍵按一下每個主控件執行個體，然後按一下**刪除**。</span><span class="sxs-lookup"><span data-stu-id="8654d-107">Right-click each host instance and click **Delete**.</span></span>  
  
2.  <span data-ttu-id="8654d-108">使用 BizTalk 管理主控台中，刪除 biztalkserverisolatedhost 主控件的協調流程伺服器主控件執行個體：</span><span class="sxs-lookup"><span data-stu-id="8654d-108">Using the BizTalk Administration Console, delete the orchestration servers host instances from the BizTalkServerIsolatedHost host:</span></span>  
  
    -   <span data-ttu-id="8654d-109">以滑鼠右鍵按一下每個主控件執行個體，並按一下 [刪除]。</span><span class="sxs-lookup"><span data-stu-id="8654d-109">Right-click each host instance and click Delete.</span></span>  
  
3.  <span data-ttu-id="8654d-110">設定主機之後，重新啟動所有伺服器上的所有主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="8654d-110">After you have configured the hosts, restart all the host instances on all the servers.</span></span>