---
title: BAM 組態結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [BAM], scaling
- scaling, BAM
- BAM, scaling
- configuration schema [BAM]
ms.assetid: 7eeeb07f-012e-44eb-a8b5-06e374946e2d
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b0d73435dc0245c3c3ce2b1574aa5a70b468c60
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230222"
---
# <a name="bam-configuration-schema"></a>BAM 組態結構描述
BAM 組態結構描述定義了 XML 文件，其中包含 BAM 管理公用程式用以部署的基礎結構之相關資訊。 您可以將資料庫部署至多部伺服器以獲致延展性。 為了支援此延展性，請確定 BAM 組態 XML 文件中包含了個別的伺服器名稱，以及下列資料庫的組態設定：  
  
-   BAMPrimaryImport  
  
-   BAMStarSchema  
  
-   BAMAnalysis  
  
-   BAMArchive  
  
## <a name="in-this-section"></a>本節內容  
  
-   [BAM DTS 封裝](../core/bam-dts-packages.md)  
  
## <a name="see-also"></a>另請參閱  
 [變更 BAM 執行階段設定](../core/changing-bam-runtime-settings.md)