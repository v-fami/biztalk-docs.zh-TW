---
title: 安裝和設定 BizTalk Accelerator for SWIFT 協調流程伺服器上 |Microsoft Docs
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
ms.openlocfilehash: 6811d3dd79de75968b3976b7568075158017609d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985079"
---
# <a name="installing-and-configuring-biztalk-accelerator-for-swift-on-orchestration-servers"></a>安裝和設定 BizTalk Accelerator for SWIFT 協調流程伺服器上
本章節描述如何安裝和設定[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]協調流程伺服器上。 這些伺服器主要用來執行 FIN 修復和重新調整的協調流程與訊息修復/新增提交協調流程。  

### <a name="to-install-and-configure-biztalk-accelerator-for-swift-on-the-orchestration-server"></a>安裝和設定 BizTalk Accelerator for SWIFT，協調流程伺服器上  

1. 執行自訂安裝[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]。 安裝**MRSR**功能。  

   > [!NOTE]
   >  您不需要安裝 Web 元件 Message Repair 和 New Submission 的功能，因為此伺服器並沒有 MRSR 站台。  

   > [!NOTE]
   >  安裝完成後，便會啟動 [組態精靈]。  

2. 在 Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]組態主控台中，設定**MCRR**。
