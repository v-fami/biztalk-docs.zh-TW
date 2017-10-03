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
# <a name="configuring-the-biztalkapplicationserver-and-biztalkserverisolatedhost-hosts"></a>設定 BizTalkApplicationServer 與 BizTalkServerIsolatedHost 主控件
若要限制的訊息 （傳送和接收訊息） 到 BizTalk 傳訊的伺服器，您需要設定預設的主控件，哪些執行 MSMQT 傳送及接收處理常式，只在訊息的伺服器上執行。  
  
### <a name="to-configure-the-default-hosts"></a>若要設定預設的主控件  
  
1.  使用 BizTalk 管理主控台，從 BizTalkApplicationServer 主機刪除協調流程伺服器主控件執行個體：  
  
    -   以滑鼠右鍵按一下每個主控件執行個體，然後按一下**停止**。  
  
    -   以滑鼠右鍵按一下每個主控件執行個體，然後按一下**刪除**。  
  
2.  使用 BizTalk 管理主控台中，刪除 biztalkserverisolatedhost 主控件的協調流程伺服器主控件執行個體：  
  
    -   以滑鼠右鍵按一下每個主控件執行個體，並按一下 [刪除]。  
  
3.  設定主機之後，重新啟動所有伺服器上的所有主控件執行個體。