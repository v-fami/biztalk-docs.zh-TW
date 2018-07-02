---
title: 安裝和設定 BizTalk Server 傳訊的伺服器上 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BizTalk Server, installing on BizTalk Messaging servers
- BizTalk Server, configuring
- BizTalk Messaging servers, configuring BizTalk Server
- BizTalk Messaging servers, installing BizTalk Server
ms.assetid: 8aaa1b97-90f0-4317-9403-ac8b5b9f80e3
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b5f4013c1fe315646ea7a2ff34772169a03a2d66
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989567"
---
# <a name="installing-and-configuring-biztalk-server-on-the-messaging-server"></a>安裝和設定 BizTalk Server 傳訊的伺服器上
本節說明如何安裝和設定 BizTalk Server 來作為郵件伺服器連線至 SWIFT 的網路。  

### <a name="to-install-and-configure-biztalk-server-on-the-messaging-server"></a>安裝和設定 BizTalk Server 傳訊伺服器上  

1. 執行自訂安裝的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]選擇 EDI、 人力工作流程服務 (HWS) 和 MRSR 網站除外的所有功能，除非所需的其他應用程式。  

   > [!NOTE]
   >  請注意，在單一電腦部署中，這台電腦所執行的 HTTP 前端服務的同一部電腦。  

2. 執行設定[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  

   > [!NOTE]
   >  請勿安裝訊息佇列，因為我們將會安裝[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]又稱為 MSMQT 的 MSMQ 版本。 MSMQT 的詳細資訊，請參閱 BizTalk 訊息佇列配接器 (MSMQT) 組態，在 MSDN 網站上[ http://go.microsoft.com/fwlink/?LinkID=48875 ](http://go.microsoft.com/fwlink/?LinkID=48875)。  

3. 安裝所需的任何其他 hotfix[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]可用的安裝指南。 在此發行集時，沒有必要的 hotfix。
