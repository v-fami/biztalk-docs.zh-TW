---
title: 安裝和設定 BizTalk Server 協調流程伺服器上 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BizTalk Server, installing on orchestration server
- orchestration server, installing BizTalk Server
ms.assetid: 72376a80-1377-4058-9478-fee668b804d0
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ecd5e9e4be9c9274a402b54a5bf6a2eba4ed73cc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984095"
---
# <a name="installing-and-configuring-biztalk-server-on-the-orchestration-servers"></a>安裝和設定 BizTalk Server 協調流程伺服器上
本節說明如何安裝和設定 BizTalk Server 來執行訊息修復/新增提交協調流程和 FIN 修復和重新調整協調流程，與協調流程伺服器使用。  

### <a name="to-install-and-configure-biztalk-server-on-the-orchestration-server"></a>安裝和設定 BizTalk Server 協調流程伺服器上  

1. 執行自訂安裝的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]選擇 EDI、 人力工作流程服務 (HWS) 和 MRSR，除外的所有功能，除非所需的其他應用程式。  

   > [!NOTE]
   >  在單一電腦部署中，此電腦是指執行 HTTP 前端服務 」 和 「 BizTalk 傳訊伺服器在同一部電腦。  

2. 執行設定[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  

   > [!NOTE]
   >  設定 BizTalk 協調流程伺服器時，請考慮下列指導方針：  

   - 此伺服器需要的只有一個網路介面卡，以將其連接到[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]電腦。 它不需要像 HTTP 前端伺服器或傳訊伺服器上，在公用端上的另一個網路介面卡，因此更安全，抵禦攔截企圖來自網際網路或內部網路/外部網路。  

3. 安裝所需的任何其他 hotfix[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]可用的安裝指南。
