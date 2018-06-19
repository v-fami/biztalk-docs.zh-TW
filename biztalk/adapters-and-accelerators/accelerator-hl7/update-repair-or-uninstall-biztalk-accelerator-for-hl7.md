---
title: 更新、 修復或解除安裝 BizTalk Accelerator for HL7 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e2fc84d2-1262-4a6e-ae9c-488a00ab4099
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5b4fa1dba322e830114a76a0ca69134edbb1d06
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
ms.locfileid: "25962172"
---
# <a name="update-repair-or-uninstall-biztalk-accelerator-for-hl7"></a>更新、 修復或解除安裝 BizTalk Accelerator for HL7

變更、 修復或解除安裝[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]。  
  
> [!IMPORTANT]
>  確定要解除安裝[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]再解除安裝[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]無法解除安裝，如果[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]不會再安裝。  

## <a name="prerequisites"></a>필수 구성 요소
* 使用成員的帳戶登入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。  

* 此使用者帳戶也必須是 Administrators 群組的成員上[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]儲存 BizTalk Accelerator for HL7 資料。  
    
## <a name="update-an-existing-installation"></a>更新現有的安裝

> [!NOTE]
>  當您修改您的安裝[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]，端對端教學課程不會自動執行。 
> 
> 若要執行本教學課程，並確認已正確執行修改過的安裝，執行本教學課程以手動方式從***\<磁碟機\>*** **\Program Files\Microsoft BizTalk \<版本\>Accelerator for HL7\SDK\End 端對端教學課程**資料夾。
  
1. 執行[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] **setup.exe**身為系統管理員 
  
2.  在 [歡迎使用] 頁面上，選取**下一步**。  
  
3.  在**程式維護**，選取**修改**，然後選取**下一步**。  
  
4.  在**自訂安裝程式**、 選取您想要安裝的功能、 清除功能您不想，，然後選取**下一步**。  
  
5.  在 [摘要] 選取**下一步**。  
  
6.  選取 [安裝]。  
  
7. 完成後，請選取 [完成]。  

## <a name="repair-an-existing-installation"></a>修復現有安裝
[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]精靈會修正遺失或損毀的檔案、 捷徑或登錄項目，修復安裝。  
  
1. 執行[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] **setup.exe**以系統管理員身分。  
  
2.  在 [歡迎使用] 頁面上，選取**下一步**。  
  
3.  在**程式維護**，選取**修復**，然後選取**下一步**。  
  
4.  在**記錄服務帳戶**，重新輸入使用者帳戶，並選取**確定**。  
  
4.  如果出現提示**帳戶名稱已被授與登入為服務右**，然後選取**確定**繼續。  
  
5.  當準備好修復時，選取**安裝**。  
  
6. 完成時，選取**完成**。 

  
## <a name="uninstall-btahl7"></a>解除安裝 BTAHL7  

> [!IMPORTANT]
>  如果沒有接收位置或使用 MLLP 傳輸類型的傳送埠，BTAHL7 安裝程式不會移除 MLLP 配接器在解除安裝 BTAHL7 期間。 解除安裝之前，移除所有接收位置或傳送埠使用 MLLP 傳輸。 或者，您也可以將傳輸類型 mllp 變更為另一種類型。 然後，解除安裝將會移除 MLLP 配接器。  
      
1.  開啟 [程式和功能]。  
  
2.  選取[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]，然後選取**解除安裝**。  
  
4.  選取**是**如果要求確認。 
  
5.  完成時，選取**完成**。  
  
    > [!NOTE]
    >  BTAHL7 不會自動解除安裝[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]成品和組件。  
  

  
## <a name="troubleshooting-installation-issues"></a>疑難排解安裝問題  
 如果伺服器是無法驗證使用者是否為[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]系統管理員，請解除安裝 BTAHL7 會傳回下列錯誤： 
 
 `Fatal error during uninstallation`  
  
若要繼續解除安裝，執行下列作業：  
  
1.  以本機系統管理員身分登入伺服器。  
  
2.  解除安裝 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  
  
3.  解除安裝 [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]。  
  
## <a name="see-also"></a>另請參閱  
[安裝或升級 Microsoft BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-or-upgrade-microsoft-biztalk-accelerator-for-hl7.md)