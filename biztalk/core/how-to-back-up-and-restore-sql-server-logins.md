---
title: 如何備份和還原 SQL Server 登入 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 847c3a3d-0d97-415b-893e-4ba173085bae
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54fa6a51a27f82add8a96c613e36f5ed7ce88e87
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248550"
---
# <a name="how-to-back-up-and-restore-sql-server-logins"></a>如何備份和還原 SQL Server 登入
備份和還原 BizTalk Server 相關聯的 SQL Server 登入。  
  
## <a name="biztalk-server-sql-server-security-logins"></a>BizTalk Server SQL Server 安全性登入  
 下面所列的 SQL Server 安全性登入是 BizTalk Server 相關聯。 您可能與您所建立的 BizTalk Server 應用程式相關聯的其他登入。 您需要備份登入，並將 BizTalk Server 資料庫移到新的伺服器或 SQL Server 的新執行個體時還原它們。  
  
-   BizTalk 應用程式使用者  
  
-   BizTalk 外掛式主控件使用者  
  
-   BizTalk Server 系統管理員  
  
-   BizTalk Server 操作員  
  
-   SSO 系統管理員  

## <a name="prerequisites"></a>必要條件  
您必須是成員**管理員**您備份並還原登入的 SQL Server 上的安全性角色。  
  
## <a name="back-up-a-login-using-a-script"></a>備份使用指令碼的登入  
  
1.  開啟**SQL Server Management Studio**。  
  
2.  展開**安全性**，並展開的清單**登入**。  
  
3.  以滑鼠右鍵按一下您想要建立的備份指令碼，然後選取 登的入**以指令碼登入**。  
  
4.  選取**CREATE 至**，然後選取其中一個**新增查詢編輯器視窗**，**檔案**，或**剪貼簿**選取指令碼的目的地。 通常，目的地是檔案之 **.sql**延伸模組。  
  
5.  重複此程序步驟 3 從每個登入您想要編寫指令碼。 清單，請參閱 BizTalk Server 的相關登入，以便判斷哪些登入，您需要指令碼。  
  
## <a name="restore-a-login-from-a-script"></a>從指令碼還原登入  
  
1.  開啟**SQL Server Management Studio**。  
  
2.  在**檔案**功能表上，**開啟**包含已編寫指令碼的登入的檔案。  
  
3.  執行建立登入指令碼。