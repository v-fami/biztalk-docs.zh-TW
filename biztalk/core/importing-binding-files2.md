---
title: "匯入繫結 Files2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding files, importing
- assemblies, removing from database
- importing binding files
- target computers, cleaning
- BizTalk assemblies, removing from database
ms.assetid: 9e552a4b-06ec-4887-b17b-a625c137699f
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3783b21385c210c454bcd3d4c951f2200a6ec866
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="importing-binding-files"></a>匯入繫結檔案
本節提供有關部署 BizTalk Adapter for JD Edwards EnterpriseOne 時之匯入程序的資訊。 當您在目標電腦上重新部署繫結檔案 (和組件)，傳送埠和接收位置會在重新匯入 XML 繫結檔案時，被取代為 XML 繫結檔案中的傳送埠和接收位置。  
  
### <a name="to-clean-the-target-computer"></a>若要清除目標電腦  
  
-   移除協調流程所繫結的傳送埠和接收位置。  
  
     如果目標電腦上未安裝 Visual Studio，您可以執行下列指令碼來移除連接埠：  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\  
  
     Remove Send Port\VBScript\RemoveSendPort.vbs  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\  
  
     Remove Receive Port\VBScript\RemoveReceivePort.vbs  
  
     例如，在命令提示字元下執行：  
  
     **cscript RemoveSendPort.vbs\<傳送埠名稱 >**  
  
## <a name="see-also"></a>另請參閱  
 [部署連接埠和組件](../core/deploying-ports-and-assemblies3.md)