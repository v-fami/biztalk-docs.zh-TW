---
title: ExportBindings 命令 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6573142e-7ca7-4990-98e3-b7a54840da13
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 478a1c75a1e47a801d47ef9f9481a00931d37ecf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971831"
---
# <a name="exportbindings-command"></a>ExportBindings 命令
匯出 BizTalk 組件、應用程式或群組的繫結。 您也可以連同組件、應用程式或群組一併匯出全域合作對象繫結 (合作對象是與協調流程互動的所有實體，例如貴組織的夥伴)。  
  
## <a name="usage"></a>使用方式  
 **BTSTask ExportBindings /Destination:** *值*[**/GroupLevel**] [**/ApplicationName:**<em>值</em>] [**/AssemblyName:**<em>值</em>] &#124; [**/GlobalParties**] [**/Server:**<em>值</em>] [**/Database:**<em>值</em>]  
  
## <a name="parameters"></a>參數  
  
|參數|必要項|ReplTest1|  
|---------------|--------------|-----------|  
|**/ 目的地**(或 **/De**，請參閱 < 備註 >)|是|要建立的繫結檔案完整路徑 (包含檔案名稱)。 如果具有相同路徑的繫結檔案已存在，將會覆寫檔案。 如果路徑包含空格，您必須將它括在雙引號 (") 中。|  
|**/ GroupLevel** (或 **/Gr**，請參閱 < 備註 >)|否|如果有指定，將匯出目前群組的所有繫結。 下列三個參數只能指定其中之一：GroupLevel、ApplicationName 或 AssemblyName。|  
|**/ ApplicationName** (或 **/Ap**，請參閱 < 備註 >)|否|要匯出其繫結的應用程式名稱。 應用程式必須存在。 如果名稱包含空格，您必須將它括在雙引號 (") 中。 若要確認應用程式名稱，您可以使用**ListApps**命令，如中所述[ListApps 命令](../core/listapps-command.md)。 如果沒有指定這個參數，將會使用預設的 BizTalk 應用程式。 下列三個參數只能指定其中之一：GroupLevel、ApplicationName 或 AssemblyName。|  
|**/ AssemblyName** (或 **/As**，請參閱 < 備註 >)|否|要匯出其繫結的組件的本機唯一識別碼 (LUID)。 您也可以使用應用程式中檢視成品的 Luid 清單[ListApp 命令](../core/listapp-command.md)。 下列三個參數只能指定其中之一：GroupLevel、ApplicationName 或 AssemblyName。|  
|**/ GlobalParties** (或 **/Gl**，請參閱 < 備註 >)|否|如果有指定，將匯出群組的全域合作對象資訊。|  
|**/Server** (或 **/S**，請參閱 < 備註 >)|否|裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。<br /><br /> 只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。 只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。<br /><br /> 範例:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> 如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。|  
|**/ 資料庫**(或 **/Da**，請參閱 < 備註 >)|否|BizTalk 管理資料庫的名稱。 如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。|  
  
## <a name="sample"></a>範例  
 **/Destination BTSTask ExportBindings:"C:\Binding Files\MyBindings.xml"GroupLevel /Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
## <a name="remarks"></a>備註  
 參數不區分大小寫。 您不需要輸入整個參數名稱來指定它；您可以輸入參數名稱的前幾個字母，只要能明確識別就好了。  
  
## <a name="see-also"></a>另請參閱  
 [BTSTask 命令列參考](../core/btstask-command-line-reference.md)   
 [匯出繫結](../core/exporting-bindings6.md)