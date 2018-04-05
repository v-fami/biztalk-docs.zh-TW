---
title: 如何使用.NET 組件做為資料來源 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Business Rule Composer, data sources
ms.assetid: 14dbec48-acc9-4c3c-bd7f-737dabf29543
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fa56370cf894d0d18a36320ca97c4d028fee487
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-a-net-assembly-as-a-data-source"></a>如何使用 .NET 組件做為資料來源
您可以指定 .NET 組件作為資料來源。 然後從組件選取類別或類別成員，將它拖曳至詞彙定義或規則中。  
  
### <a name="to-specify-a-net-assembly-as-a-data-source"></a>指定 .NET 組件作為資料來源  
  
1.  在 事實總管 視窗中，按一下**.NET 類別** 索引標籤。  
  
2.  以滑鼠右鍵按一下**模組**節點。  
  
3.  從可用的組件中選取 .NET 組件。  
  
    > [!NOTE]
    >  組件必須位在全域組件快取 (GAC) 中。 當您瀏覽.NET 組件中，「 商務規則編輯器 」 會載入.NET 組件**事實總管**視窗或在**.NET 類別或類別成員定義**頁面**詞彙定義**視窗。  如果您在 GAC 中更新此組件，請關閉商務規則編輯器並將它重新啟動，以載入更新的 .NET 組件。 商務規則編輯器並不會自動重新整理此組件。  
  
     ![事實和定義樹狀結構瀏覽器的螢幕擷取畫面。] (../core/media/ebiz-netbrowse.gif "ebiz_netbrowse")