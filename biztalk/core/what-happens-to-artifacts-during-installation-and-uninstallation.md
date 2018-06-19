---
title: 會發生什麼事成品安裝和解除安裝期間 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- uninstalling, artifacts
- artifacts, uninstalling
- installing, artifacts
- artifacts, installing
- uninstalling
ms.assetid: f7b5bd8b-bfdf-4536-ae64-fa98c4885be6
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6274c32656ddece5a0afd81317538126d48b2f89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22289638"
---
# <a name="what-happens-to-artifacts-during-installation-and-uninstallation"></a>安裝和解除安裝期間成品所發生的狀況
本主題說明當您安裝和解除安裝應用程式時，BizTalk Server 如何處理包含在 BizTalk 應用程式中以檔案為基礎的成品。  
  
> [!NOTE]
>  傳送埠、傳送埠群組、接收位置和接收埠並不是以檔案為基礎的成品，且不會受到安裝和解除安裝的影響。 協調流程、結構描述、對應和管線都會被當做包含它們的 BizTalk 組件的一部分來進行部署及管理。  
  
-   **BizTalk 組件。** ：在安裝期間，BizTalk 組件檔會複製到目的路徑 (如果將組件加入至應用程式時有指定目的路徑)。 如果在新增組件時指定要將其安裝到全域組件快取 (GAC)，則也會將組件安裝到 GAC 中。 當應用程式解除安裝時，組件檔會從檔案系統中刪除 (如果檔案系統中有組件檔)，但不會從 GAC 解除安裝，除非開發人員在應用程式中加入後置處理指令碼來執行這項作業。 必要時可以手動方式從 GAC 中解除安裝 BizTalk 組件。 如需詳細資訊，請參閱[如何從 GAC 解除安裝組件](http://msdn.microsoft.com/library/464706a8-f902-4d05-a724-19169facd2b4)。  
  
-   **.NET 組件。** ：在安裝期間，.NET 組件檔會複製到目的路徑 (如果將組件加入至應用程式時有指定目的路徑)。 如果在新增組件時指定要將其安裝到 GAC 和 Windows 登錄，則也會將組件安裝到這些位置。 當應用程式解除安裝時，如果組件檔案是存在於檔案系統 (而不是 Windows Registry) 中，就會從檔案系統刪除。 組件不會從 GAC 或 Windows 登錄中移除，除非開發人員在應用程式中加入後置處理指令碼來執行這項作業。 必要時可以手動方式從 GAC 或 Windows 登錄中移除 BizTalk 組件。 如需詳細資訊，請參閱[如何從 GAC 解除安裝組件](http://msdn.microsoft.com/library/464706a8-f902-4d05-a724-19169facd2b4)和[如何移除其他檔案和設定 BizTalk 應用程式](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md)。  
  
-   **檔案。** ：在安裝期間，檔案會複製到本機檔案系統 (如果將檔案加入至應用程式時有指定目的路徑)。 將應用程式解除安裝時，資料將從檔案系統中刪除。  
  
-   **憑證。** ：在安裝期間，憑證會新增至本機電腦上的「其他人」憑證存放區。 將應用程式解除安裝時，憑證不會移除，除非開發人員在應用程式中加入後置處理指令碼來執行這項作業。 必要時可以手動移除憑證。 如需詳細資訊，請參閱[如何移除其他檔案和設定 BizTalk 應用程式](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md)。  
  
-   **虛擬目錄。** ：如果電腦上安裝應用程式的位置有 Internet Information Services (IIS) 存在，就會建立虛擬目錄。 如果已經有具有相同名稱、且使用指定連接埠的虛擬目錄存在，應用程式 .msi 檔案中的虛擬目錄資源就會寫入現有的虛擬目錄，而現有虛擬目錄的安全性設定會保留不變更。 您應驗證這些安全性設定是否足夠。 如果當您安裝應用程式時，虛擬目錄繫結至的應用程式集區不存在於本機電腦上，則虛擬目錄會繫結至預設的應用程式集區。  
  
     在解除安裝應用程式時，會刪除虛擬目錄和其檔案，除非虛擬目錄在安裝之前就已存在，或者檔案已在安裝之後新增至虛擬目錄。 在此案例中，只會刪除從應用程式 .msi 檔案所安裝的檔案。 不會刪除虛擬目錄以及在應用程式安裝之後新增至該目錄的檔案。 只有虛擬目錄是空白時，才會將其刪除。  
  
-   **COM 元件。** ：在安裝期間，COM 元件會新增至 Windows 登錄 (如果將元件新增至應用程式時有指定這個選項)。 此外，如果將元件新增至應用程式時有指定目的地位置，則會將檔案複製到本機檔案系統。 在解決安裝應用程式時，不會從 Windows 登錄或檔案系統中移除 COM 元件，除非開發人員在應用程式中加入後置處理指令碼來執行這項功能。 必要時可以手動方式從 Windows 登錄和檔案系統中移除 COM 元件。 如需詳細資訊，請參閱[如何移除其他檔案和設定 BizTalk 應用程式](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md)。  
  
-   **前置處理和後置處理指令碼。** ：在安裝期間，指令碼檔案會複製到本機檔案系統 (如果將檔案加入至應用程式時有指定目的路徑)。 前置處理指令碼是在應用程式匯入或移除之前，或在解除安裝之後執行。 後置處理指令碼則是在應用程式匯入或移除之後，或在安裝之後執行。 將應用程式解除安裝時，指令碼檔案將從檔案系統中刪除。 不過，如果前置或後置處理指令碼是將檔案新增至檔案系統，則這些檔案不會刪除。 必要時可以手動刪除檔案。 如需詳細資訊，請參閱[如何移除其他檔案和設定 BizTalk 應用程式](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md)。  
  
-   **BAM 成品。** ：在安裝期間，BAM 成品檔案會複製到目的路徑 (將成品加入至應用程式時所指定的路徑)。 在安裝應用程式時並不會部署 BAM 成品。 在解除安裝應用程式時會刪除 BAM 成品。  
  
## <a name="see-also"></a>另請參閱  
 [如何安裝 BizTalk 應用程式](../core/how-to-install-a-biztalk-application.md)   
 [如何解除安裝 BizTalk 應用程式](../core/how-to-uninstall-a-biztalk-application.md)   
 [會發生什麼事成品至應用程式部署期間](../core/what-happens-to-artifacts-during-application-deployment.md)