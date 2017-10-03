---
title: "如何將憑證新增至應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications, certificates
- managing [certificates], adding to applications
- certificates, applications
- managing [applications], certificates
- managing [certificates], applications
- managing [resources], certificates
ms.assetid: 7c615002-6627-4134-9c2b-bf1c89d626c2
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7551e18b1e63f706dfe7e5ff8f951e7aee4f4694
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-certificate-to-an-application"></a>如何將憑證新增至應用程式
本主題說明如何使用命令列，將憑證加入至 BizTalk 應用程式。 BizTalk Server 管理主控台上無法使用這個選項。 您可以將憑證加入至 BizTalk 應用程式，如此就可以將憑證封裝於應用程式中，從一個 BizTalk 群組傳輸到另一個群組。 您可以使用憑證，確認識別並建立傳送埠和接收位置的安全連結。 如需詳細資訊，請參閱[如何指派憑證給傳送埠](../core/how-to-assign-a-certificate-to-a-send-port.md)和[如何指派憑證給接收位置](../core/how-to-assign-a-certificate-to-a-receive-location.md)。  
  
 當您新增憑證至應用程式時，請牢記下列要點：  
  
-   將憑證加入至應用程式時，憑證會加入至 BizTalk 管理資料庫做為憑證成品。 安裝應用程式時，會將憑證匯入至本機電腦上的 [其他人] 憑證存放區，所以您不需要採取其他步驟將它匯入這個存放區，即可將它指派給傳送埠或接收位置。 使用 BTSTask 加入憑證時，憑證必須存在於 [其他人] 憑證存放區，而且您必須指定其指紋。  
  
    > [!NOTE]
    >  在匯出憑證時，會移除私密金鑰。 在安裝應用程式時，會將憑證匯入至憑證存放區，但不能用它來解密加密的訊息 (可用來傳送加密訊息)。 如果憑證必須用於前面的用途，您應該在裝載使用憑證之傳送埠的電腦上，將它重新安裝在 [其他人] 憑證存放區。  
  
-   最佳作法是，如果憑證由兩個以上之應用程式中的傳送埠或接收位置使用，您應該將該憑證部署到個別的應用程式中，然後從需要使用該憑證的應用程式參考此應用程式。 這是因為 BizTalk 群組中只能存在一個具有特定指紋的憑證，所以您將無法在兩個不同的應用程式中匯入相同的憑證。 如果您嘗試匯入使用相同憑證的兩個應用程式，第一個匯入會成功，第二個匯入則會失敗。 在此情況下，使用覆寫匯入選項無法修正此問題，因為您想要覆寫的現有憑證包含在另一個應用程式中。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-add-a-certificate-to-an-application"></a>若要新增憑證至應用程式  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別`cmd`，然後按一下 **確定**。  
  
2.  輸入下列命令，並以適當的值替代，如下表所述：  
  
     **BTSTask AddResource** [**/ApplicationName:***值*] **/Type:System.BizTalk:Certificate** [**/Overwrite**] **/Thumbprint:"***值***"** [**/Server:***值*] [**/Database:***值*]  
  
     範例：  
  
     **BTSTask AddResource /applicationname: myapplication /Type:System.BizTalk:Certificate /Overwrite /Thumbprint:"04 a2 8e 32 24 f9 36 b9 42 81 12 71 3a d2 ef db c7 9 c 83 dc"/Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
    |參數|值|  
    |---------------|-----------|  
    |**/ 應用程式名稱**|加入憑證的 BizTalk 應用程式的名稱。 若未指定應用程式名稱，將使用群組預設的 BizTalk 應用程式。 如果名稱包含空格，您必須將它括在雙引號 (") 中。|  
    |**/ 類型**|**System.biztalk: certificate** （此值不區分大小寫）。|  
    |**/ 覆寫**|此選項指定更新現有的憑證。 若未指定此選項，且應用程式中現有的憑證其 [指紋] 屬性與所加入的憑證相同，加入作業將會失敗。 若要查看 [指紋] 屬性，請在 [憑證] 嵌入式管理單元中按兩下憑證，然後按一下 [詳細資料] 索引標籤。如需詳細資訊，請參閱 [憑證] 嵌入式管理單元說明文件中的＜檢視憑證資訊＞。|  
    |**/ 憑證指紋**|憑證指紋屬性 (*指紋*是資料的摘要)。 此值必須括在雙引號 (") 中。|  
    |**/ 伺服器**|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
    |**/ 資料庫**|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="see-also"></a>另請參閱  
 [管理.NET 組件、 憑證和其他資源](../core/managing-net-assemblies-certificates-and-other-resources.md)   
 [AddResource 命令： 憑證](../core/addresource-command-certificate.md)   
 [建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md)