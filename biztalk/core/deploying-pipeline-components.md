---
title: "將管線元件部署 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, pipeline components [custom]
- pipeline components [custom], deploying
ms.assetid: 98b47fbf-62c0-4012-a406-58c4d56b305a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 041bd8c6e6fa9c3969be18f0804460c00de5f11a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="deploying-pipeline-components"></a>部署管線元件
所有.NET 管線元件組件 （原生和自訂） 必須都位於\<*安裝目錄*\>\Pipeline Components 資料夾執行的伺服器。 如果具有自訂元件的管線將要在數台伺服器之間部署，該元件的二進位檔必須存在於每一部伺服器上的指定資料夾中。  
  
 您不需要將 BizTalk 執行階段所要使用的自訂管線元件加入到全域組件快取 (GAC)。  
  
 此管線中的自訂 COM 元件也會出現在工具箱中 (前提是這些元件會在電腦上註冊為 COM 元件)。 自訂.NET 管線元件必須放入\<*安裝目錄*\>\Pipeline Components 資料夾。  
  
 當二進位檔位於正確的位置之後，您需要將此元件新增至工具箱。 如需新增管線元件至工具箱的指示，請參閱[如何使用 [工具箱]](../core/how-to-use-the-toolbox.md)。  
  
## <a name="see-also"></a>請參閱  
 [開發自訂管線元件](../core/developing-custom-pipeline-components.md)