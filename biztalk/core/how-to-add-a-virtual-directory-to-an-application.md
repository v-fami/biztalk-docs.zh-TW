---
title: "如何將虛擬目錄新增至應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- virtual directories
- managing [applications], virtual directories
- applications, virtual directories
- virtual directories, applications
ms.assetid: a5726696-bd65-49d9-8814-a078afe8c067
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26627387a65b19cef8146cee8b91b2a7a0919059
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-virtual-directory-to-an-application"></a>如何將虛擬目錄新增至應用程式
本主題描述如何使用 BTSTask 命令列工具，將虛擬目錄加入到 BizTalk 應用程式。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台上無法使用這個選項。 如果您已經撰寫自訂 Web 服務或建立 ASP.NET 網站來與 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 互動，而且您想要搭配此應用程式部署虛擬目錄，此時您可能會想要新增虛擬目錄。  
  
 中所述，另一種方式新增至應用程式的虛擬目錄是虛擬目錄指定的 SOAP 或 HTTP 接收位置，[如何設定 HTTP 接收位置](../core/how-to-configure-an-http-receive-location.md)。 在所有情況下，此虛擬目錄都會加入到 BizTalk 管理資料庫。 當您使用命令列新增虛擬目錄時，它也會顯示[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台 中您要加入它的應用程式的 [資源] 資料夾，以及當您使用應用程式中的成品清單[ListApp 命令](../core/listapp-command.md)。 如果您之後匯出此應用程式，然後將它匯入到另一個 BizTalk 群組，則此虛擬目錄會顯示在 [資源] 資料夾中。  
  
 當您將虛擬目錄加入到應用程式時，請牢記下列要點：  
  
-   您可以覆寫應用程式中現有的虛擬目錄，只要指定覆寫選項即可。 只有在現有的虛擬目錄已與您想要加入相同的名稱時，才需要覆寫選項。 如果未指定，且虛擬目錄已經存在相同名稱做為所新增的應用程式中，新增作業將會失敗。  
  
-   如果您要加入之虛擬目錄的 URL 包含 https，指定 URL 時必須改用 http 代替 https。 若是使用 https，虛擬目錄加入作業將會失敗。 雖然您在 URL 中使用 http 來加入，Internet Information Services Metabase 仍會沿用 URL 的 https 設定使之生效，因此虛擬目錄將可正常運作。  
  
-   如果您所加入的虛擬目錄來自 64 位元版的 Web 服務，而您試圖將含有該虛擬目錄的應用程式安裝於 32 位元電腦，屆時將不會安裝該虛擬目錄。 它必須安裝在 64 位元電腦上。  
  
> [!IMPORTANT]
>  當您匯入包含虛擬目錄的應用程式時，該虛擬目錄上的安全性設定就是在應用程式匯出期間產生 .msi 檔案時生效的那些安全性設定。 如果您將應用程式部署到實際執行環境，則在匯出應用程式之前，應該驗證設定是否符合安全性需求。  
>   
>  如果目的地環境中已經有虛擬目錄存在，則現有虛擬目錄上的安全性設定將會生效。 這些設定不會為了要與您部署之虛擬目錄上的設定相符而變更。 在此情況下，您應該驗證現有虛擬目錄上的安全性設定是否符合您的需求。  
  
> [!CAUTION]
>  如果虛擬目錄使用的是 HTTPS (超文字安全傳輸通訊協定) 通訊協定，則在匯出期間不會保留其安全性設定，而且在匯入時，虛擬目錄會繼承根目錄的安全性設定。 您應該驗證這些安全性設定是否符合您的需求。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-add-a-virtual-directory-to-an-application"></a>若要將虛擬目錄加入至應用程式  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別`cmd`，然後按一下**確定**。  
  
2.  輸入下列命令，並以適當的值替代，如下表所述：  
  
     **BTSTask AddResource** [/**ApplicationName:***值*] **/Type:System.BizTalk:WebDirectory**[**/Overwrite**] **/Source:***值*[**/Destination:***值*] [**/Server:** *值*] [**/database:***值*]  
  
     範例：  
  
     **BTSTask AddResource /applicationname: myapplication/類型： system.biztalk: webdirectory / 覆寫 /Source:http://Host1:90 / MyVirtualDirectory /Destination:http://Host2:90 / MyVirtualDirectory /Server:MyDatabaseServer/資料庫：BizTalkMgmtDb**  
  
    |參數|值|  
    |---------------|-----------|  
    |**/ 應用程式名稱**|加入虛擬目錄的 BizTalk 應用程式名稱。 若未指定應用程式名稱，將使用群組預設的 BizTalk 應用程式。 如果名稱包含空格，您必須將它括在雙引號 (") 中。|  
    |**/ 類型**|**System.biztalk: webdirectory** （此值不區分大小寫）。|  
    |**/ 覆寫**|更新現有虛擬目錄的選項。 若未指定此選項，且應用程式中現有的虛擬目錄與所加入的虛擬目錄同名，AddResources 作業將會失敗。|  
    |**/ 來源**|來源虛擬目錄的 URI。|  
    |**/ 目的地**|從 .msi 檔案安裝應用程式時，指派給虛擬目錄的 URI。 若未指定此參數，將使用 Source 參數的值並以 localhost 做為主控件。|  
    |**/ 伺服器**|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
    |**/ 資料庫**|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="see-also"></a>另請參閱  
 [管理.NET 組件、 憑證和其他資源](../core/managing-net-assemblies-certificates-and-other-resources.md)   
 [AddResource 命令： 虛擬目錄](../core/addresource-command-virtual-directory.md)   
 [建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md)