---
title: ListTypes 命令 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94febe8a-4c1e-4581-a6d1-ef579633e745
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: afe2519fc5507ae0975d050a998faec78f2940a3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262214"
---
# <a name="listtypes-command"></a>ListTypes 命令
列出所有的成品類型，您可以加入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用**AddResource**命令。 如需有關**AddResource**命令，請參閱[AddResource 命令](../core/addresource-command.md)。  
  
 受支援成品類型的完整格式名稱如下：  
  
-   .NET 組件：System.BizTalk:Assembly  
  
-   BAM 定義：System.BizTalk:Bam  
  
-   BizTalk 組件：System.BizTalk:BizTalkAssembly  
  
-   BizTalk 繫結檔案：System.BizTalk:BizTalkBinding  
  
-   安全性憑證：System.BizTalk:Certificate  
  
-   COM 元件：System.BizTalk:Com  
  
-   臨機操作檔案：System.BizTalk:File  
  
-   後置處理指令碼：System.BizTalk:PostProcessingScript  
  
-   前置處理指令碼：System.BizTalk:PreProcessingScript  
  
-   原則或規則：System.BizTalk:Rules  
  
-   虛擬目錄：System.BizTalk:WebDirectory  
  
> [!NOTE]
>  為避免命名空間衝突，請始終使用完整類型名稱 (例如 System.BizTalk:Assembly)，切勿單僅使用類型名稱 (例如 Assembly)。  
  
## <a name="usage"></a>使用方式  
 **BTSTask ListTypes**  
  
## <a name="see-also"></a>另請參閱  
 [BTSTask 命令列參考](../core/btstask-command-line-reference.md)