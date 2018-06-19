---
title: SQL Server 和配接器的用戶端上設定 MSDTC |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2c87f455-a8c4-4169-bf18-695926136df1
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf519044dc28d417d85682189dd4a52585310ac0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222918"
---
# <a name="configure-msdtc-on-sql-server-and-adapter-client"></a>SQL Server 和配接器的用戶端上設定 MSDTC
使用 SQL Server 上執行的操作[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] (透過[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，WCF 服務模型或 WCF 通道模型) 可以在交易範圍內執行。 如果用戶端程式有多個交易的資源做為在相同交易的一部分，在交易取得提高 MSDTC 交易。 若要啟用的介面卡來執行 MSDTC 交易的範圍內的作業，您必須執行的電腦上設定 MSDTC 這兩個[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]和 SQL Server。 此外，您必須將 MSDTC 加入 Windows 防火牆的例外狀況清單。 本節提供如何在執行配接器用戶端和 SQL Server 的電腦上執行這些工作的相關資訊。  
  
> [!NOTE]
>  使用 SQL Server 上執行的作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]一律牽涉到兩個資源，配接器連接到 SQL Server 和 SQL Server 上的 BizTalk 訊息方塊。 因此，所有作業都執行使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]MSDTC 交易的範圍內都執行。 因此，為了使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您必須一律啟用 MSDTC。  
  
> [!NOTE]
>  作業在配接器用戶端就無法寫入任何資料的 SQL Server 資料庫，選取的作業，例如，您可能不想執行的作業在交易內的額外負擔。 在這種情況下，您可以設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]執行沒有交易式內容的作業，藉由設定**UseAmbientTransaction**內容繫結至**false**。 如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。 在這種情況下，您不需要也將 MSDTC 設定。  
  
## <a name="configure-msdtc"></a>設定 MSDTC  
  
1.  開啟**元件服務**。  

    或者，在**伺服器管理員**，選取**工具**，然後選取**元件服務**。  
  
2.  展開**元件服務**，依序展開**電腦**，依序展開**我的電腦**，依序展開**分散式交易協調器**，以滑鼠右鍵按一下**本機 DTC**，然後選取**屬性**。  
  
3.  選取 **[安全性]** 索引標籤。在此索引標籤上，選取下列各項： 

  - **網路 DTC 存取**
  - **允許遠端用戶端** 
  - **允許輸入** 
  - **允許輸出** 
  - **沒有所需的 Authetnication**
  
4.  選取 [確定] 儲存您的變更。  
  
5.  如果提示您重新啟動 MSDTC 服務，請選取**是**。 重新啟動 MSDTC 服務之後，關閉屬性和元件服務 MMC。 
  
## <a name="add-msdtc-to-windows-firewall-exceptions-list"></a>加入 Windows 防火牆例外清單中的 MSDTC  

> [!TIP] 
>  Microsoft 分散式 Tansaction 協調器 (MSDTC) 可能已經能在防火牆中。 如果是的話，它被顯示為輸入的規則。 如果未列出，請使用本節以允許 MSDTC。 

1.  開啟**Windows 防火牆**，然後選取**進階設定**左側。  

    或者，在**伺服器管理員**，選取**工具**，然後選取**具有進階安全性的 Windows 防火牆**。  
  
2.  以滑鼠右鍵按一下**輸入規則**，然後選取**新規則**。  
  
3.  在精靈中： 

    1. 選取**程式**，然後選取**下一步**。 
    2. 設定**程式路徑**至`%SystemRoot%\system32\msdtc.exe`，然後選取**下一步**。  
    3. **允許連線**，然後選取**下一步**。
    4. 選取**網域**，然後選取**下一步**。
    5. 輸入任何名稱，例如`MSDTC for Oracle EBS`，然後選取**完成**。
  
5.  完成精靈，並關閉 Windows 防火牆。 
  
## <a name="see-also"></a>另請參閱  
[開發 SQL 應用程式](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)