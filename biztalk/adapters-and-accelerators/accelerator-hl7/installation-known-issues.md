---
title: 安裝已知問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b2f80ff9-b37c-49f8-8250-fcf3cec4c0fc
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4f017fa273d91d1c40727ba34c6d047383054d52
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000919"
---
# <a name="installation-known-issues"></a>安裝已知問題
有用的資訊可協助您避免安裝問題。  
  
## <a name="prerequisites-for-installing-btahl7"></a>安裝 BTAHL7 的必要條件  
 安裝的先決條件[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]包含下列項目：  
  
- 基本元件[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，包括企業單一登入 (SSO)、 群組和執行階段應該設定。  
  
- 安裝和設定 BTAHL7 使用者必須是 BizTalk 系統管理員群組的成員和儲存 BTAHL7 資料的 SQL Server 上的 Administrators 群組的成員。
  
## <a name="sql-server-mixed-mode-not-supported"></a>不支援的 SQL Server 混合的模式  
[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]不支援混合模式中的 SQL Server。  
  
## <a name="repair-does-not-work-from-uninstallchange"></a>修復無法解除安裝/變更程式運作  
如果已啟用使用者存取控制 (UAC)，而且您嘗試修復您使用控制台中的安裝，修復就會失敗。 

Microsoft 建議您持續啟用 UAC。

 **解決方式**  
  
 執行[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]setup.exe，然後選取**修復**。  
  
## <a name="see-also"></a>另請參閱  
[安裝或升級 Microsoft BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-or-upgrade-microsoft-biztalk-accelerator-for-hl7.md)