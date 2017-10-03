---
title: "ListPackage 命令 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be09b76b-429b-4639-89f0-1eadb0c851ce
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88fca4820dba7c04908e2b756fda0d1d25794a10
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="listpackage-command"></a>ListPackage 命令
列出 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 產生的 .msi 檔案中所包含的成品。  
  
## <a name="usage"></a>使用方式  
 **BTSTask ListPackage** [**/封裝：***值*]  
  
## <a name="parameters"></a>參數  
  
|參數|Required|Description|  
|---------------|--------------|-----------------|  
|**/ 封裝**或  **/P**|是|.msi 檔案的名稱和路徑。 範例： C:\MSI\MyApplication.msi。 如果路徑包含空格，則它必須括在雙引號 （"）。|  
  
## <a name="sample"></a>範例  
 **ListPackage /Package:"C:\My MSI Files\MyApplication.msi"**  
  
## <a name="remarks"></a>備註  
 參數不區分大小寫。 您不需要輸入整個參數名稱來指定它；您可以輸入參數名稱的前幾個字母，只要能明確識別就好了。  
  
## <a name="see-also"></a>另請參閱  
 [BTSTask 命令列參考](../core/btstask-command-line-reference.md)