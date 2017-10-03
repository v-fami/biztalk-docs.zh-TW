---
title: "設定 A4SWIFT 使用者 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, user accounts
- creating, user accounts
- user accounts, creating
ms.assetid: 45dcbece-ec8d-410a-8320-79bfbc4c779d
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79c3b63cd77bb34545f4c4093796310aa7720563
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-a4swift-users"></a>設定 A4SWIFT 使用者
在安裝期間[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]，A4SWIFT 組態程式會建立預設交易夥伴設定檔和協議，並註冊 BizTalk Server。 A4SWIFT 也會建立 Message Repair 和 New Submission 元件所使用的文件庫。  
  
 A4SWIFT 安裝期間建立的下列文件資料夾：  
  
-   寄件匣文件庫  
  
-   範本文件庫  
  
-   未剖析的文件庫  
  
-   新的 SWIFT MT 訊息文件庫  
  
-   新的 SWIFT MX 訊息文件庫  
  
 建立每個部門，A4SWIFT 系統管理員必須手動設定網站的相對應的部門的群組和 A4SWIFT 定義角色。 每個部門/角色有自動建立設定檔 Web Client(PWC) 收件匣。  
  
 A4SWIFT 安裝組態程式完成之後，A4SWIFT 系統管理員會設定工作流程中每個部門的組織中。 訊息修復和新送出在設定期間，設定檔的 Web 用戶端，透過對應的收件匣會建立每個部門/角色組合。 比方說，PWC 組態期間 A4SWIFT 系統管理員會建立名為付款的部門，並再將建立者、 Repairers 和核准者的角色指派給呼叫付款的部門。 MRSR 站台上的文件庫會使用名稱來建立收件匣中的範例下表, 所示：  
  
|部門名稱|角色名稱|收件匣名稱|  
|---------------------|---------------|----------------|  
|付款|建立者|Payments_Creator|  
|付款|Repairers|Payments_Repairers|  
|付款|核准者|Payments_Approvers|