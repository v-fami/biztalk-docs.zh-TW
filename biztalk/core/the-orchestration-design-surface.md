---
title: 協調流程設計介面 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5fb190b-60d7-45e4-9883-7b3d2ed6b0c0
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f943c1543cf50e4ecb1f25627cbccd7b4d72eab5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279806"
---
# <a name="the-orchestration-design-surface"></a>協調流程設計介面
協調流程設計介面是一套可以用來建立 BizTalk 協調流程的視覺化設計工具，也是協調流程設計師的中央元件。 它是一張畫布，可以讓您從工具箱拖曳圖形到上面，然後再設定圖形。 這個設計介面是 Visual Studio 編輯器視窗，所以會佔用其他 Visual Studio 編輯器視窗所使用的主視窗區域。  
  
 ![協調流程設計師](../core/media/b96c16e5-58a2-4d8e-b66c-485864846cec.gif "b96c16e5-58a2-4d8e-b66c-485864846cec")  
協調流程設計介面  
  
 協調流程的名稱會顯示在 [協調流程設計介面] 視窗最上方的索引標籤上，以及 Visual Studio 視窗的標題列上。  
  
 在設計介面本身分成三個區域: 「 處理區域和兩個連接埠介面 」。 中央的「處理區域」包含會描述協調流程之實際處理流程的圖形。 Flanked 兩端的連接埠介面 」，其中包含只連接埠和角色連結圖形互動**傳送**和**接收**處理區域 中的圖形。  
  
 **流程領域**  
  
 「處理區域」是協調流程設計師之協調流程設計介面的主要部分，永遠位於協調流程設計介面的水平置中位置。  
  
 「處理區域」的兩邊都是「連接埠介面」。 **開始**圖形位於設計介面的頂端和協調流程會隨著向下加入圖形。  
  
 **連接埠介面**  
  
 協調流程設計介面中會顯示兩個「連接埠介面」，分別位於「處理區域」兩側。 連接埠介面 」 可以包含兩種類型的圖形：**連接埠**和**角色連結**。 這些圖形互動**傳送**和**接收**處理區域 中的圖形。  
  
 不論您將使用哪個「連接埠介面」來處理圖形，都不會造成任何差異，圖形在左右「連接埠介面」上的功能都一樣。 有了這個可以放置新連接埠的「連接埠介面」，您就可以建立交叉接點較少且更容易管理的協調流程。  
  
 這兩個「連接埠介面」都可以摺疊或展開，方法是按兩下介面或是按一下雙箭頭圖示。  
  
> [!IMPORTANT]
>  在許多協調流程設計師工作中，您都必須選取各種不同的項目，例如結構描述或協調流程。 如果這些項目不在目前的專案中，請務必記得在您的專案中加入組件的參考，且參考的組件必須包含您想要選取的項目。 若要這樣做，請以滑鼠右鍵按一下專案，然後選取**加入參考**。  
  
 **支援縮放**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提供縮放協調流程設計師介面的功能。 如果要使用縮放支援，請完成下列其中一個步驟：  
  
-   以滑鼠右鍵按一下協調流程設計師介面，然後按一下**縮放**功能表選項。 接著，您可以選取想要套用的縮放比例。  
  
-   使用 CTRL + 滑鼠滾輪的組合以放大或縮小。按住 CTRL 鍵，同時上下轉動滑鼠滾輪。 使用 CTRL+滑鼠滾輪上移的組合可將介面縮小，CTRL+滑鼠滾輪下移的組合則可將介面放大。