---
title: "安裝和設定 BizTalk Server 傳訊的伺服器上 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Server, installing on BizTalk Messaging servers
- BizTalk Server, configuring
- BizTalk Messaging servers, configuring BizTalk Server
- BizTalk Messaging servers, installing BizTalk Server
ms.assetid: 8aaa1b97-90f0-4317-9403-ac8b5b9f80e3
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2db4b3d5ff34a724b8b37a08f0bf60807d31a2b2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="installing-and-configuring-biztalk-server-on-the-messaging-server"></a>安裝和設定 BizTalk Server 傳訊的伺服器上
本章節描述如何安裝及設定[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]来做為郵件伺服器連線到 SWIFT 網路。  
  
### <a name="to-install-and-configure-biztalk-server-on-the-messaging-server"></a>安裝和設定 BizTalk Server 傳訊的伺服器上  
  
1.  執行自訂安裝的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]選擇 EDI、 人力工作流程服務 (HWS) 和 MRSR 網站之外的所有功能，除非需要其他應用程式。  
  
    > [!NOTE]
    >  請注意，在單一電腦部署中，此電腦是一個執行 HTTP 前端服務的同一部電腦。  
  
2.  執行設定[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  
  
    > [!NOTE]
    >  請勿安裝訊息佇列，因為我們將需要安裝[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]又稱為 MSMQT 的 MSMQ 版本。 MSMQT 的詳細資訊，請參閱 BizTalk 訊息佇列配接器 (MSMQT) 設定，在 MSDN 網站上[http://go.microsoft.com/fwlink/?LinkID=48875](http://go.microsoft.com/fwlink/?LinkID=48875)。  
  
3.  安裝所需的任何其他 hotfix[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]為可用安裝指南中。 在此發行集時，有不必要的 hotfix。