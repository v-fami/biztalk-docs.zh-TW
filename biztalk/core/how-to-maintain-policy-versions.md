---
title: 如何維護原則版本 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- policies, publishing
- publishing policies
- updating, policies
- versioning, policies
- policies, versioning
- policies, updating
ms.assetid: 6e35b2bd-1ecd-45ea-aff3-4ad2437568a4
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 09c73b3575ec484ab611fccac920cef6d96d3800
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254494"
---
# <a name="how-to-maintain-policy-versions"></a>如何維護原則版本
將規則新增至原則版本後，可以將版本儲存至規則存放區以供進一步開發之用，或是您可以將它發佈以建立定義正確且不變，可加以部署以用於以規則為基礎的應用程式中的規則集。  
  
 本主題包含下列工作的程序：  
  
-   建立空的原則新版本  
  
-   儲存原則版本  
  
-   發佈原則版本  
  
-   建立更新的原則版本  
  
-   更新原則以使用更新的組件  
  
### <a name="to-create-an-empty-new-version-of-a-policy"></a>建立空的原則新版本  
  
-   以滑鼠右鍵按一下 [原則] 資料夾，然後按一下**新增版本**。  
  
### <a name="to-save-a-policy-version"></a>儲存原則版本  
  
-   以滑鼠右鍵按一下原則版本，然後**儲存**。  
  
### <a name="to-publish-a-policy-version"></a>發佈原則版本  
  
-   以滑鼠右鍵按一下原則版本，然後**發行**。  
  
### <a name="to-create-an-updated-version-of-a-policy"></a>建立更新的原則版本  
  
1.  以滑鼠右鍵按一下現有的原則版本，然後按一下**複製**。  
  
2.  以滑鼠右鍵按一下 [原則] 資料夾，然後按一下**貼上**。  
  
     具有與複製版本相同項目的新版本已建立。  
  
    > [!NOTE]
    >  若原則使用 .NET 組件且組件已更新，則應該將原則繫結至較新版本的組件。  
  
### <a name="to-update-a-policy-to-use-an-updated-assembly"></a>更新原則以使用更新的組件  
  
1.  按一下**啟動**，指向 **系統管理工具**，指向  **.NET Framework 組態**，然後按一下 **設定的組件**.  
  
2.  移至屬性的目標組件，然後按一下**繫結原則** 索引標籤。  
  
3.  在全域組件快取中，將版本號碼變更為較新的版本。  
  
    > [!NOTE]
    >  原則使用的所有組件應該會新增至全域組件快取。