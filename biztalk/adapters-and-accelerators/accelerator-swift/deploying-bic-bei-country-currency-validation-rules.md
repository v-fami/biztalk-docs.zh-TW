---
title: 部署驗證 BIC BEI 國家/地區-貨幣規則 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2e96d416-d5eb-4597-a691-c7dbee33c7d6
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57bdaa8f2a13b650019fa02b096ca05971389570
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25964580"
---
# <a name="deploying-bicbeicountrycurrency-validation-rules"></a>部署 BIC/BEI/國家/地區/貨幣驗證規則
**若要部署的 BIC/BEI/國家/地區/貨幣驗證規則：**  
  
1.  下列的一組原則，%program files%\Microsoft BizTalk Accelerator for SWIFT\SDK\MX Messages\Base 原則，也就是要發行和部署個別的一般和不特定訊息，需要使用商務規則引擎部署精靈。  
  
    -   MX_BIC_Master_Policy.xml  
  
    -   MX_BIC_Validation_Policy.xml  
  
    -   MX_BEI_Validation_Policy.xml  
  
    -   MX_DBConnection_Master_Policy.xml  
  
    -   MX_BICPlusIBAN_Validation_Policy.xml  
  
    -   MX_SEPA_Validation_Policy.xml  
  
2.  部署這些原則之前, MX_DBConnection_Master_Policy.xml 和 MX_BIC_Master_Policy.xml 應有資料庫伺服器名稱和資料庫名稱的國家/地區/貨幣值已儲存的位置。  
  
3.  一旦已修改的主要原則，發佈所有原則使用商務規則引擎部署精靈 」。 使用下列選項： 原則/詞彙檔案匯入資料庫。  
  
4.  按一下 程式中，按一下 BizTalk Server\<版本\>，按一下 商務規則編輯器，然後部署已發佈的六個原則。