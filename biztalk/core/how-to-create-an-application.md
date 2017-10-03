---
title: "如何建立應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications, creating
- creating, applications
ms.assetid: 6a8682a7-3bef-4978-996f-5a9c5154ce62
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6078e292673a1d9dbe3634ea9c0c4e79ab9c2cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-an-application"></a>如何建立應用程式
有三個方法可建立新的 BizTalk 應用程式：  
  
-   使用 BizTalk Server 管理主控台的 [新增應用程式] 命令或 BTSTask 命令列工具的 AddApp 命令，建立 BizTalk 應用程式。 本主題稍後將提供執行此作業的程序。  
  
-   匯入已經從另一個應用程式匯出的 .msi 檔案。 如果目前 BizTalk 群組中沒有此應用程式，則會在目前 BizTalk 群組中自動建立此應用程式以及它的成品。 如需詳細資訊，請參閱[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。  
  
-   從 Visual Studio 將 BizTalk 組件部署到 BizTalk 應用程式。 如果目前 BizTalk 群組中沒有 Visual Studio 所指定的應用程式，則會自動建立它。 如需詳細資訊，請參閱[從到 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)。  
  
 建立新應用程式之前，您可能想要決定如何設定下列選項：  
  
-   **如何命名新的應用程式。** BizTalk 群組中的每個應用程式都必須有唯一名稱。  
  
-   **是否需要加入任何其他應用程式的參考。** 若要在這個應用程式中重複使用其他應用程式中的成品，您必須在此應用程式中新增其他應用程式的參考。 這會建立應用程式之間的相依性，也會影響您必須部署這些應用程式的方式。 如需背景資訊，請參閱[相依性和應用程式部署](../core/dependencies-and-application-deployment.md)和[如何加入另一個應用程式的參考](../core/how-to-add-a-reference-to-another-application.md)。  
  
-   **是否需要建立多個應用程式。** 您可能需要將一些成品部署至個別的應用程式。 例如，共用的成品應部署至專屬、個別的應用程式。 如需詳細資訊，請參閱[部署 BizTalk 應用程式的最佳作法](../core/best-practices-for-deploying-a-biztalk-application.md)。  
  
 當您建立應用程式之後時，您可以將成品新增到它，並進行其他修改，本節中的其他主題中所述 ([建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md))。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="to-create-a-biztalk-application"></a>若要建立 BizTalk 應用程式  
  
#### <a name="using-the-biztalk-server-administration-console"></a>使用 BizTalk Server 管理主控台  
  
1.  按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，以滑鼠右鍵按一下您要建立新的應用程式，指向 BizTalk 群組**新增**，然後按一下 **應用程式**。  
  
3.  在**名稱**，輸入應用程式的名稱。 此名稱必須是 BizTalk 群組中唯一的名稱。  
  
4.  如果您想要將此 BizTalk 群組的預設應用程式，選取**設預設應用程式**核取方塊。  
  
5.  在**描述**，輸入應用程式的描述。  
  
6.  如果此應用程式會重複使用另一個應用程式的成品，請按一下**參考**和其餘的步驟。 否則，請按一下**確定**並採取任何進一步的步驟。  
  
7.  按一下**新增**，選取包含您想要重複使用此應用程式，然後按一下的成品的應用程式**確定**。 對每個新增應用程式參考，重複這個步驟。  
  
8.  如果您想要從清單中移除應用程式，選取的應用程式，然後按一下**移除**。  
  
9. 完成後，請按一下 **[確定]**。  
  
#### <a name="using-the-command-line"></a>使用命令列  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別`cmd`，然後按一下 **確定**。  
  
2.  輸入下列命令，並以適當的值替代，如下表所述：  
  
     **BTSTask AddApp /ApplicationName:** *值*[**/預設**] [**/Description:***值*] [**/伺服器：***值*] [**/database:***值*]  
  
     範例：  
  
     **BTSTask AddApp /applicationname: myapplication /Description: 「 我最愛的應用程式 」 /Server:MySQLServer /Database:BizTalkMgmtDb**  
  
    |參數|值|  
    |---------------|-----------|  
    |**/ 應用程式名稱**|要建立的應用程式名稱。 名稱如果包含空格，則必須括在雙引號 (") 中。|  
    |**/ 預設值**|如果有指定，新應用程式將成為 BizTalk 群組預設的應用程式。|  
    |**/ 描述**|應用程式的說明。 說明如果包含空格，則必須括在雙引號 (") 中。|  
    |**/ 伺服器**|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
    |**/ 資料庫**|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="see-also"></a>另請參閱  
 [建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md)   
 [AddApp 命令](../core/addapp-command.md)