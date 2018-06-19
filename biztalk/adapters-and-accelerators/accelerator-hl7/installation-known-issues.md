---
title: 安裝的已知問題 |Microsoft 文件
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
ms.openlocfilehash: bf4e9197d2b3c448b4fd9cc42c0cdeb929917061
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204542"
---
# <a name="installation-known-issues"></a>安裝的已知問題
有用的資訊可協助您避免安裝問題。  
  
## <a name="prerequisites-for-installing-btahl7"></a>安裝 BTAHL7 的必要條件  
 安裝的必要條件[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]如下：  
  
-   基本元件[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，包括企業單一登入 (SSO)、 群組和執行階段應該設定。  
  
-   安裝和設定 BTAHL7 使用者必須是 BizTalk 系統管理員群組的成員，並儲存 BTAHL7 資料的 SQL Server 上的 Administrators 群組的成員。
  
## <a name="sql-server-mixed-mode-not-supported"></a>不支援的 SQL Server 混合的模式  
[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]不支援 SQL Server 混合模式中。  
  
## <a name="repair-does-not-work-from-uninstallchange"></a>修復無法解除安裝/變更程式運作  
如果使用者存取控制 (UAC) 已啟用，而且您嘗試修復您安裝使用控制台中，修復就會失敗。 

Microsoft 建議您保持啟用 UAC。

 **解決方式**  
  
 執行[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]setup.exe，然後選取**修復**。  
  
## <a name="see-also"></a>另請參閱  
[安裝或升級 Microsoft BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-or-upgrade-microsoft-biztalk-accelerator-for-hl7.md)