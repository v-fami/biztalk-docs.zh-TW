---
title: "如何清除目標 Computer1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, removing
- send ports, removing
- cleaning target computer
ms.assetid: 78986a33-3c77-48dc-88c4-b78f52911c22
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7adf1761b6eb31ce158232c22af457b9c716a812
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-clean-the-target-computer"></a>如何清除目標電腦
部署會覆寫接收位置組態。 當您在目標電腦上部署繫結檔案 (和組件)，在匯入 XML 繫結檔案時，傳送埠和接收位置會被 XML 繫結檔案中的傳送埠和接收位置所取代。  
  
### <a name="to-clean-the-target-computer"></a>若要清除目標電腦  
  
-   移除協調流程所繫結的傳送埠和接收位置。  
  
     如果目標電腦上尚未安裝 Microsoft Visual Studio，您可以執行下列指令碼來移除連接埠：  
  
    -   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs  
  
    -   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs  
  
         例如，在命令提示字元下執行：  
  
         **cscript RemoveSendPort.vbs\<傳送埠名稱 >**  
  
## <a name="see-also"></a>另請參閱  
 [部署連接埠和組件](../core/deploying-ports-and-assemblies1.md)