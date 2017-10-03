---
title: "安裝和設定 BizTalk Server 協調流程伺服器上 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Server, installing on orchestration server
- orchestration server, installing BizTalk Server
ms.assetid: 72376a80-1377-4058-9478-fee668b804d0
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d872d58c72110d7af22c6d64e7d212fbee53fae9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="installing-and-configuring-biztalk-server-on-the-orchestration-servers"></a>安裝和設定 BizTalk Server 協調流程伺服器上
本章節描述如何安裝及設定[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]要做為協調流程伺服器用於執行訊息修復/新增提交協調流程和 FIN 修復和重新調整協調流程。  
  
### <a name="to-install-and-configure-biztalk-server-on-the-orchestration-server"></a>安裝和設定 BizTalk Server 協調流程伺服器上  
  
1.  執行自訂安裝的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]選擇 EDI、 人力工作流程服務 (HWS) 和 MRSR，以外的所有功能，除非需要其他應用程式。  
  
    > [!NOTE]
    >  在單一電腦部署中，此電腦是指執行 HTTP 前端服務和 BizTalk 傳訊的伺服器在同一部電腦。  
  
2.  執行設定[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  
  
    > [!NOTE]
    >  設定 BizTalk 協調流程伺服器時，請考慮下列指導方針：  
  
    -   此伺服器需要只有一個網路介面卡連線到[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]電腦。 不需要像 HTTP 前端伺服器或訊息的伺服器，在公用端的另一個網路介面卡，因此針對駭客嘗試從網際網路或內部/外部網路更安全。  
  
3.  安裝所需的任何其他 hotfix[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]為可用安裝指南中。