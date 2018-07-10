---
title: 移轉和升級疑難排解 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- upgrading, troubleshooting
- troubleshooting, upgrading
- troubleshooting, migrating
- migrating, troubleshooting
ms.assetid: 6e6c0ff9-7897-4de6-9e9b-b502b3a1785b
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ad7f575038257bc876e3fc822e624e91c93451ff
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994639"
---
# <a name="migration-and-upgrade-troubleshooting"></a>移轉和升級疑難排解
## <a name="assemblies-need-to-be-undeployed-before-an-upgrade"></a>需要升級之前解除部署組件  
  
### <a name="symptom"></a>徵兆  
 當您嘗試升級 A4SWIFT 時，升級程序將會失敗。  
  
### <a name="possible-cause"></a>可能的原因  
 下列的 A4SWIFT 組件仍會部署在完成升級時： Microsoft.Solutions.FinancialServices.SWIFT.FrrOrchestration、 Microsoft.Solutions.FinancialServices.SWIFT.FrrSchemas，Microsoft.Solutions.FinancialServices.SWIFT.MrsrService。  
  
> [!NOTE]
>  您不必重新部署 Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas。 安裝程式重新部署該組件。  
  
### <a name="solution"></a>方案  
 手動解除部署四個 A4SWIFT 組件，以下列順序：  
  
- Microsoft.Solutions.FinancialServices.SWIFT.FrrOrchestration  
  
- Microsoft.Solutions.FinancialServices.SWIFT.FrrSchemas  
  
- Microsoft.Solutions.FinancialServices.SWIFT.MrsrService.  
  
  升級之後，重新部署這些組件 (使用**BTSTask.exe**) 的相反順序。  
  
## <a name="an-upgrade-removes-access-permissions-for-the-service-folder"></a>升級會移除服務資料夾的存取權限  
  
### <a name="symptom"></a>徵兆  
 若要在升級之後[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]，%programfiles%\Microsoft BizTalk Accelerator for SWIFT\Service 資料夾的存取權限不正確。  
  
### <a name="possible-cause"></a>可能的原因  
 當您升級至[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]，升級程序會移除 %programfiles%\Microsoft BizTalk Accelerator for SWIFT\Service 資料夾中的 [A4SWIFT 系統管理員] 和 [A4SWIFT 使用者群組的存取權限。  
  
### <a name="solution"></a>方案  
 如果您遇到這個問題，以手動方式設定下列服務資料夾的存取權限：  
  
|群組或使用者名稱|權限|  
|------------------------|----------------|  
|A4SWIFT 系統管理員|完整控制|  
|A4SWIFT 使用者|閱讀及執行|  
  
 若要設定這些權限，請繼續進行，如下所示：  
  
 在 [[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管] 中，移至 *%programfiles%* \Microsoft BizTalk Accelerator for SWIFT\Service。  
  
1.  以滑鼠右鍵按一下 服務 資料夾中，按一下**屬性**，然後按一下**安全性** 索引標籤。  
  
2.  在 群組或使用者名稱 窗格的 服務內容 對話方塊中，按一下**新增**，輸入 ***\<伺服器名稱\>* \A4SWIFT 管理員**，然後按一下  **確定**.  
  
    > [!NOTE]
    >  如果 A4SWIFT Administrators 群組的網域群組，請輸入 ***\<網域名稱\>* \A4SWIFT 管理員**。  
  
3.  重複步驟 2 ***\<伺服器名稱\>* \A4SWIFT 使用者**，或 **\<*網域名稱*\>\A4SWIFT 使用者**如果A4SWIFT 使用者群組是網域群組。  
  
4.  在 [群組或使用者名稱] 窗格中，選取**A4SWIFT 管理員**。 在 [權限] 窗格中，選取**允許**for**完全控制**。  
  
5.  在 [群組或使用者名稱] 窗格中，選取**A4SWIFT 使用者**。 在 權限 窗格中，按一下 **允許**如**讀取與執行**，**列出資料夾內容**，以及**讀取**。  
  
6.  按一下 [確定] 。  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解：問題與解決方式](../../adapters-and-accelerators/accelerator-swift/troubleshooting-issues-and-resolutions1.md)