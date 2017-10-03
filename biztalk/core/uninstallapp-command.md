---
title: "UninstallApp 命令 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f45c9530-8138-40f1-b279-1428c5a7fbbc
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea94335882ffbcf01b69c450ef4a5eb80ef4fa3d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="uninstallapp-command"></a>UninstallApp 命令
從本機電腦解除安裝 BizTalk 應用程式，同時將應用程式從 [控制台] 的 [新增或移除程式] 所列程式清單中移除。 此命令與使用 [新增或移除程式] 移除應用程式具有同樣的效果。 如果應用程式是由多個 .msi 檔案經數次安裝，便會解除安裝所有 .msi 檔案安裝的全部項目。  
  
 使用此命令時所指定的應用程式名稱必須與 [新增或移除程式] 中顯示的應用程式名稱一致。 如果您不確定的應用程式名稱，您可以使用**ListPackage**命令來取得它，如中所述[ListPackage 命令](../core/listpackage-command.md)。  
  
> [!IMPORTANT]
>  雖然按兩下 .msi 檔案或許可以解除安裝應用程式，事實上並不支援這種做法。 其原因在於同一個應用程式可能是由多個 .msi 檔案經數次安裝，以致這種做法未必能夠解除安裝與應用程式相關聯的所有項目。  
  
## <a name="usage"></a>使用方式  
 **BTSTask UninstallApp /ApplicationName:** *值*  
  
## <a name="parameters"></a>參數  
  
|參數|Required|Description|  
|---------------|--------------|-----------------|  
|**/ ApplicationName** (或**/A**，請參閱 < 備註 >)|是|要解除安裝的 BizTalk 應用程式的名稱。 如果名稱包含空格，您必須將它括在雙引號 (") 中。|  
  
## <a name="sample"></a>範例  
 **BTSTask UninstallApp /applicationname: myapplication**  
  
## <a name="remarks"></a>備註  
 參數不區分大小寫。 您不需要輸入整個參數名稱來指定它；您可以輸入參數名稱的前幾個字母，只要能明確識別就好了。  
  
## <a name="see-also"></a>另請參閱  
 [BTSTask 命令列參考](../core/btstask-command-line-reference.md)   
 [如何解除安裝 BizTalk 應用程式](../core/how-to-uninstall-a-biztalk-application.md)