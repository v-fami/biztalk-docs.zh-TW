---
title: "如何移除 BAM 檢視 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, views
- managing [BAM definitions], deleting views
- Remove-View command [BAM]
ms.assetid: 1a43ec81-20b1-41f7-941f-753132ac9ed2
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04d8930fb4e3f2014945b743b15da4dbdfff3451
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-bam-views"></a>如何移除 BAM 檢視
系統管理員使用**移除檢視**命令，從 BAM 主要匯入資料庫移除檢視。  
  
> [!NOTE]
>  當您移除檢視時，也會自動移除該檢視所定義的任何警示。  
  
### <a name="to-remove-bam-views"></a>若要移除 BAM 檢視  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
2.  瀏覽至追蹤資料夾，輸入**C:\Program Files\Microsoft BizTalk Server 2009 \tracking**在命令提示字元。 按 ENTER 鍵。  
  
3.  型別**bm 移除檢視的名稱：\<檢視名稱 >**。  
  
4.  按 ENTER 鍵。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM 安全性建議](../core/bam-security-recommendations.md)   
 [BAM 管理公用程式](../core/bam-management-utility.md)   
 [如何移除 BAM 警示](../core/how-to-remove-bam-alerts.md)