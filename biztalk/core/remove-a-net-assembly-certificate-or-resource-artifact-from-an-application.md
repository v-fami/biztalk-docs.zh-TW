---
title: 如何從應用程式移除.NET 組件、 憑證或其他資源成品 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- virtual directories, deleting
- managing [.NET assemblies], deleting
- managing [applications], COM components
- managing [applications], deleting artifcats
- managing [certificates], deleting
- deleting, binding files
- binding files, deleting
- managing, COM components
- COM components, deleting
- managing [artifacts], deleting
- .NET assemblies, deleting
- deleting, virtual directories
- deleting, definitions [BAM]
- applications, .NET assemblies
- certificates, deleting
- deleting, .NET assemblies
- deleting, artifacts
- deleting, certificates
ms.assetid: b84eebac-261d-495f-80cd-ddda5bb08bef
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1dce140e7adeaf6115ad2f8b2199a3a77292a953
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002919"
---
# <a name="how-to-remove-a-net-assembly-certificate-or-other-resource-artifact-from-an-application"></a>如何從應用程式移除 .NET 組件、憑證或其他資源成品
本主題說明如何使用 BizTalk Server 管理主控台或命令列，從 BizTalk 應用程式移除下列資源成品。 使用本主題提供的程序可以從 BizTalk 管理資料庫移除成品， 但是不會從檔案系統、憑證存放區、Internet Information Services (IIS) 或 Windows 登錄等任何位置中，移除現有的成品。 此外，如果您移除繫結檔案，繫結仍將原封不動，而只會移除繫結檔案而已。  
  
- .NET 組件  
  
- COM 元件  
  
- 憑證  
  
- 臨機操作檔案  
  
- BAM 定義  
  
- 繫結檔案  
  
- 虛擬目錄  
  
  如果虛擬目錄是透過匯入或新增的方式，明確加入至應用程式，您可以使用本主題明的程序將它移除； 但是如果沒有明確加入，而是在設定接收位置時以參考的方式加入，則不能使用本主題中的程序移除它。 這是因為虛擬目錄不是儲存在 BizTalk 管理資料庫中。 當您匯出應用程式 .msi 檔案時，系統會從 IIS 取得虛擬目錄，並將它新增到 .msi 檔案； 而當您匯入 .msi 檔案時，虛擬目錄則會新增到該群組的 BizTalk 管理資料庫。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="to-remove-a-resource-artifact-from-an-application"></a>從應用程式移除資源成品  
  
#### <a name="using-the-biztalk-server-administration-console"></a>使用 BizTalk Server 管理主控台  
  
1. 按一下 **開始**，按一下**程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，展開 [BizTalk Server 管理]、 展開 BizTalk 群組包含之資源成品移除，然後再展開包含成品的應用程式。  
  
3. 按一下 **資源**資料夾中，以滑鼠右鍵按一下成品，然後**移除**。  
  
#### <a name="using-the-command-line"></a>使用命令列  
  
1. 開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別`cmd`，然後按一下 **確定**。  
  
2. 輸入下列命令，並以適當的值替代，如下表所述：  
  
    **BTSTask RemoveResource** [**/ApplicationName:**<em>值</em>] **/Luid:**<em>值</em>[**/Server:** <em>值</em>] [**/database:**<em>值</em>]  
  
    範例  
  
    **BTSTask RemoveResource /applicationname: myapplication /Luid:"MyAssembly，version=1.0.0.0，Culture = neutral，PublicKeyToken = 0123456789ABCDEF"**  
  
   |參數|描述|  
   |---------------|-----------------|  
   |**/ 應用程式名稱**|含有所要刪除之成品的 BizTalk 應用程式的名稱。 如果沒有指定，將會使用預設的應用程式。 如果名稱包含空格，您必須將它括在雙引號 (") 中。|  
   |**/ Luid**|成品的本機唯一識別碼 (LUID)。 您可以使用來取得 LUID **ListApp**命令，如中所述[ListApp 命令](../core/listapp-command.md)。|  
   |**/ 伺服器**|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
   |**/ 資料庫**|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="see-also"></a>另請參閱  
 [管理.NET 組件、 憑證和其他資源](../core/managing-net-assemblies-certificates-and-other-resources.md)   
 [RemoveResource 命令](../core/removeresource-command.md)