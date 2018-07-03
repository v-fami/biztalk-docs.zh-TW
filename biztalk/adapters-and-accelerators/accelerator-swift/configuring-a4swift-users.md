---
title: 設定 A4SWIFT 使用者 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security, user accounts
- creating, user accounts
- user accounts, creating
ms.assetid: 45dcbece-ec8d-410a-8320-79bfbc4c779d
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b75a3e95c836f8a577543b43319e6abe49a96c42
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005255"
---
# <a name="configuring-a4swift-users"></a>設定 A4SWIFT 使用者
在安裝期間[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]，A4SWIFT 組態程式會建立預設交易夥伴設定檔和協議，並註冊 BizTalk Server。 A4SWIFT 也會建立 Message Repair 和 New Submission 元件所使用的文件庫。  
  
 A4SWIFT 安裝期間建立下列的文件資料夾：  
  
- 寄件匣文件庫  
  
- 範本文件庫  
  
- 未剖析的文件庫  
  
- 新增 SWIFT MT 訊息文件庫  
  
- 新增 SWIFT MX 訊息文件庫  
  
  每個部門建立，A4SWIFT 系統管理員必須手動設定網站群組對應的部門，和 A4SWIFT 定義的角色。 每個部門/角色有自動建立設定檔 Web Client(PWC) 收件匣。  
  
  A4SWIFT 安裝組態程式完成之後，A4SWIFT 系統管理員會設定在組織中的每個部門的工作流程。 Message Repair 和 New Submission 在設定期間，透過設定檔的 Web 用戶端，相對應的收件匣會針對每個部門/角色組合。 比方說，PWC 組態期間 A4SWIFT 系統管理員會建立名為付款的部門使用，然後將 Creators Repairers 及核准者的角色指派給稱為付款的部門。 下表中的範例所示，MRSR 網站上的文件庫會建立與收件匣名稱：  
  
|部門名稱|角色名稱|收件匣名稱|  
|---------------------|---------------|----------------|  
|付款|建立者|Payments_Creator|  
|付款|Repairers|Payments_Repairers|  
|付款|核准者|Payments_Approvers|