---
title: "安全性和 Windows Installer |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, Windows installer
- Windows installer
ms.assetid: efa68c3e-2006-4665-bd41-07defaf4e2e2
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4418994a4b5ff705d1faef751ac8c96ba86f9dc7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="security-and-windows-installer"></a>安全性與 Windows Installer
Windows Installer 是強大的工具，可用來安裝和更新 BizTalk 應用程式。 在使用 Windows Installer 時，您應該注意可能由惡意的 Windows Installer (.msi) 檔案建立者製造的安全性問題，並採取步驟加以防止。  
  
 系統管理員通常會執行 .msi 檔案，因此在應用程式安裝或更新期間所執行的程序具有很高的權限。 惡意的 .msi 檔案建立者可能會以數種方式利用這項事實，包含以下各項：  
  
-   執行對系統或檔案進行不利變更的指令碼檔案。  
  
-   覆寫 COM 目錄。  
  
-   覆寫登錄值。 這些變更無法回復。  
  
-   灌爆檔案系統。  
  
 在處理 .msi 檔案時，應該至少考慮下列預防措施：  
  
-   只安裝您完全信任的 .msi 檔案。  
  
    > [!NOTE]
    >  最佳作法是由負責產生 .msi 檔案的人員採取額外的步驟來簽署 .msi 檔案，以讓使用者可以確認檔案來源是可信任的。  
  
-   在實際執行環境中使用 .msi 檔案之前，請徹底地加以測試。  
  
-   將 .msi 檔案儲存在受保護的資料夾中 (以適當的判別存取控制清單 (DACL) 進行保護)。  
  
## <a name="see-also"></a>另請參閱  
 [應用程式部署的安全性考量](../core/security-considerations-for-application-deployment.md)