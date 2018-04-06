---
title: 如何啟用自動封存驗證 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- validating, archives [Tracking database]
- archiving [Tracking database], validating archive
ms.assetid: 406ca54a-6b1f-4bdb-9bad-bea5ea0f6e66
caps.latest.revision: 30
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e654d22a08a7b07210ded9c319953c288065927a
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="how-to-enable-automatic-archive-validation"></a>如何啟用自動封存驗證
封存驗證讓您可以在封存建立時驗證封存。 在您可以啟用自動封存驗證前，必須先設定次要資料庫伺服器，也稱為驗證伺服器。 因為封存程序是簡單備份，所以儲存在磁碟上的實際影像可能由於硬體問題而毀損。  
  
 您可以使用封存驗證功能，確保封存 (備份) 已成功，而且可以還原。 建立封存之後，會通知驗證伺服器已經建立新的封存。 驗證伺服器會嘗試還原封存。 驗證伺服器必須是另一個執行個體[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]不同的作業在執行。 版本[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]驗證伺服器必須是相同的版本[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]用來主控資料庫。  
  
 若還原成功，則驗證伺服器會將此資訊傳回到 [BizTalk 追蹤] \(BizTalkDTADb) 資料庫。 在成功完成還原之前，清除工作不會再清除任何其他資料。  
  
 若還原不成功，則驗證伺服器會將此資訊傳回到 [BizTalk 追蹤] 資料庫。 清除工作會建立另一個封存，然後等待驗證新封存。 如此可避免毀損的封存造成追蹤資料遺失的可能性。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以成員的帳戶登入[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]sysadmin 固定的伺服器角色，才能執行此程序。  
  
### <a name="to-enable-automatic-archive-validation"></a>若要啟用自動封存驗證  
  
1.  在驗證伺服器上，按一下  **啟動**, ，按一下  **所有程式**, ，按一下  **Microsoft SQL Server 2008 SP2**, ，然後按一下  **SQL Server Management Studio**。  
  
2.  在**連接到伺服器**對話方塊方塊中，指定的名稱[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]您可以在其中執行還原程序測試來驗證封存，然後按一下**連接**連接到適當的 SQL Server。  
  
    > [!NOTE]
    >  此伺服器不應另[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]驗證封存時降低系統效能的資料庫伺服器。  
  
3.  在 **Microsoft SQL Server Management Studio**, ，按一下  **檔案**, ，按一下  **開啟**, ，然後按一下  **檔案**。  
  
4.  在 **開啟檔案**  對話方塊中，瀏覽至下列 SQL 指令碼︰  
  
    ```  
    %SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\BTS_Tracking_ValidateArchive.sql  
    ```  
  
    > [!NOTE]
    >  您可能需要從執行的電腦複製指令碼[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]來驗證伺服器。  
  
5.  按一下  **查詢** 功能表，然後再按一下 **Execute**。  
  
    > [!NOTE]
    >  只有在用於封存 BizTalk 追蹤 (BizTalkDTADb) 資料庫的資料夾為網路共用時，BTS_Tracking_ValidateArchive.sql 指令碼才能運作。  
  
     BTS_Tracking_ValidateArchive.sql 指令碼會建立稱為 ValidateArchive 的 SQL Server Agent 作業。  
  
6.  因為封存與清除程序可能會存取並 (或) 更新不同 SQL Server 中的資料庫，所以您必須在相關 SQL Server 執行個體之間設定連結的伺服器。 在 **SQL Server Management Studio**, ，連按兩下  **伺服器物件**, ，以滑鼠右鍵按一下 **連結的伺服器**, ，然後按一下  **新增連結的伺服器**。  
  
     您必須設定下列各項之間的連結伺服器：  
  
    -   每一個 BizTalk MessageBox (BizTalkMsgBoxDb) 資料庫與 BizTalk 追蹤 (BizTalkDTADb) 資料庫 (如果兩者位於不同的伺服器)。  
  
    -   [BizTalk 追蹤] (BizTalkDTADb) 資料庫與封存驗證的驗證伺服器。  
  
    -   在裝載 BizTalk MessageBox (BizTalkMsgBoxDb) 資料庫的電腦上，SQL Server 代理程式的服務帳戶必須對連結伺服器上的 BizTalk 追蹤 (BizTalkDTADb) 資料庫擁有 db_datareader 和 db_datawriter 權限。  
  
    > [!NOTE]
    >  用來執行工作的帳戶應該同時擁有兩個資料庫的 [資料庫操作員] \(DBO) 權限。  
  
7.  在 **新增連結的伺服器** 對話方塊的  **一般** 頁面上，於 **連結的伺服器**, ，輸入您想要連結至伺服器的名稱。  
  
     例如，裝載 BizTalk MessageBox (BizTalkMsgBoxDb) 資料庫、BizTalk 追蹤 (BizTalkDTADb) 資料庫或驗證伺服器的伺服器。  
  
8.  在 **伺服器類型**, ，按一下  **SQL Server**, ，然後按一下  **確定**。  
  
9. 在 **Microsoft SQL Server Management Studio**, ，連按兩下  **SQL Server Agent**, ，然後按一下  **工作**。  
  
10. 在 **物件總管詳細資料** ] 窗格中，以滑鼠右鍵按一下 **ValidateArchive**, ，然後按一下 [ **屬性**。  
  
11. 在 **作業屬性-validatearchive** 對話方塊的  **選取頁面**, ，按一下  **步驟**。  
  
12. 在 **作業步驟清單**, ，按一下  **驗證**, ，然後按一下  **編輯**。  
  
13. 在 **一般** 頁面上，於 **命令**  方塊中的，在命令中， **exec dtasp_ValidateArchive null，null**, ，取代 null，null 的裝載 BizTalk 追蹤資料庫，以單引號括住，後面加上 BizTalk 追蹤資料庫，以引號括住，括住的名稱括住的伺服器名稱，然後按一下 **確定**。 例如：  
  
     **exec dtasp_ValidateArchive '** *\<TrackingServerName\>* **', '** *\<TrackingDatabaseName\>* **'**  
  
> [!NOTE]
>  [ValidateArchive] 作業沒有排程，您不可設定它的排程。 而是由 [DTA 清除和封存] \(BizTalkDTADb) 作業在建立封存時自動啟動此作業。  
  
## <a name="see-also"></a>另請參閱  
 [封存和清除 BizTalk 追蹤資料庫](../core/archiving-and-purging-the-biztalk-tracking-database.md)