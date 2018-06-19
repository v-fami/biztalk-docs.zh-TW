---
title: 如何判斷和設定活動事件寫入者角色 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73bfe8ff-167a-4bf0-ab87-3926290d52d8
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc9fa663d395fc36205e137da374f17cb9470521
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249862"
---
# <a name="how-to-determine-and-set-event-writer-roles-for-activities"></a>如何判斷和設定活動的事件寫入者角色
在寫入活動的事件時，BAM 提供兩種安全性模式。 您可以授與個別活動的寫入事件權限，或授與所有已部署活動的寫入事件權限。  
  
 活動層級的安全性是由活動事件寫入者角色提供，當您部署 BAM 定義時可建立這些角色。 例如，如果您針對名為 CreditCard 的活動部署定義，BAM 就會建立名為 bam_CreditCard_EventWriter 的事件寫入者角色。 這個角色有寫入此活動之事件的權限。 若要授與使用者寫入此活動之事件的權限，您可以將使用者加入至此角色。  
  
 或者，您可以授與使用者的寫入權限 eve2nts 所有活動新增到超級角色 BAM_EVENT_WRITER，已寫入所有活動的權限。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行此程序，您必須有下列項目：  
  
-   連線到已部署活動的 BAMPrimaryImportDb。  
  
-   在資料庫上的 DBO 權限。  
  
### <a name="to-add-a-user-to-an-event-writer-role"></a>若要將使用者加入至事件寫入者角色  
  
1.  按一下**啟動**，指向 **所有程式**，按一下  **Microsoft SQL Server 2008**，然後按一下  **SQL Server Management Studio**。  
  
2.  在**連接到 SQL Server**對話方塊中，選取 SQL Server 和適當的驗證方法，，然後按一下**連接**。  
  
3.  在**物件總管 中**窗格中展開**資料庫**，然後選取 BAM 主要匯入資料庫。  
  
4.  按一下**新查詢**工具列上的圖示。  
  
5.  複製下列命令並將它們貼入 [查詢視窗]。 用適當值取代網域名稱、使用者名稱和活動名稱預留位置。  
  
    ```  
    EXEC sp_grantlogin '<domain name>\<user name>’  
    EXEC sp_grantdbaccess '<domain name>\<user name>', 'ActivityLogin'  
    EXEC sp_addrolemember 'bam_<activity name>_EventWriter', 'SpecialLogin'  
    ```  
  
    > [!IMPORTANT]
    >  角色名稱區分大小寫。 活動名稱也區分大小寫，也就是說，它們必須符合在部署活動時使用的大小寫。  
  
6.  按一下**Execute**圖示的工具列或按 f5 鍵執行命令。  
  
### <a name="to-add-a-user-to-an-event-writer-super-role"></a>若要將使用者加入至事件寫入者超級角色  
  
1.  按一下**啟動**，指向 **所有程式**，按一下  **Microsoft SQL Server 2008**，然後按一下  **SQL Server Management Studio**。  
  
2.  在**連接到 SQL Server**對話方塊中，選取 SQL Server 和適當的驗證方法，，然後按一下**連接**。  
  
3.  在**物件總管 中**窗格中展開**資料庫**，然後選取 BAM 主要匯入資料庫。  
  
4.  按一下**新查詢**工具列上的圖示。  
  
5.  複製下列命令並將它們貼入 [查詢視窗]。 用適當的值取代網域名稱和使用者名稱。  
  
    ```  
    EXEC sp_grantlogin '<domain name>\<user name>’  
    EXEC sp_grantdbaccess '<domain name>\<user name>', 'ActivityLogin'  
    EXEC sp_addrolemember 'BAM_EVENT_WRITER', 'SpecialLogin'  
    ```  
  
    > [!IMPORTANT]
    >  角色名稱區分大小寫。 您必須依照指示來指定事件寫入者角色。  
  
6.  按一下**Execute**圖示的工具列或按 f5 鍵執行命令。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BAM 安全性](../core/managing-bam-security.md)