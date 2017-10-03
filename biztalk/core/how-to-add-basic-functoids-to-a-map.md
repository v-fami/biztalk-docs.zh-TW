---
title: "如何新增基本運算質至對應 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a81fb73-cccf-4f74-af92-39e4af13e255
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 23a6748a5ce128ef13ce012412e36570e4e01eba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-basic-functoids-to-a-map"></a>如何新增基本運算質至對應
許多運算質都很易於使用。 這些稱為這裡以便區別中的運算質的基本運算質**進階**類別目錄。 基本運算質組成其餘的類別，例如轉換、 累計、 資料庫、 日期和時間、 邏輯、 數學、 科學，以及字串運算質。  
  
 一般而言，基本運算質有一些簡單的型別 (例如數字和字串) 作為其輸入和輸出連結。  
  
 使用基本運算質包含將它新增至格線頁，建立從左邊輸入至運算質的連結，並建立從運算質輸出至右邊的連結。 本主題提供這些作業的逐步指示。  
  
## <a name="add-a-basic-functoid-to-a-map"></a>新增基本運算質至對應  
  
1.  在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 工具箱啟用的情況下，按一下適當的索引標籤，以選取您要使用的運算質類別。  
  
     顯示所選擇類別中的可用運算質清單。  
  
2.  將所要使用的運算質從工具箱拖曳至格線頁的適當位置。  
  
    > [!NOTE]
    >  運算質將放置在顯示的格線頁上。 若要將運算質放在其他格線頁上，必須先顯示該格線頁。  
  
    > [!NOTE]
    >  若您同時使用一個以上的運算質來建構對應，您必須考慮其左右相對位置。 運算質是由左至右執行。 某個運算質的輸出，只能是其較右邊另一個運算質的輸入。  
  
## <a name="create-input-links-to-a-basic-functoid"></a>建立基本運算質的輸入的連結  
  
1.  將記錄或欄位節點從來源結構描述拖曳至顯示的格線頁中的基本運算質。  
  
     **-或者-**  
  
     在顯示的格線頁中，拖曳另一個運算質，會遠位於左邊，您要建立輸入的連結的基本運算質。  
  
     **-或者-**  
  
     將顯示的格線頁中的基本運算質拖曳至來源結構描述中的記錄或欄位節點。  
  
     **-或者-**  
  
     在顯示的格線頁中，將您要建立輸入連結的基本運算質拖曳另一個位於左邊較遠的運算質。  
  
    > [!NOTE]
    >  在拖曳時，與錨定的連結結束點相對的移動連結結束點，會變成十字形狀圖示以允許更精確地鎖定第二個結束點。 若您將移動的連結結束點暫留在不適當的第二個連結結束點的物件上，十字形狀圖示就會變成有斜線劃過的圓圈圖示 (例如，當資料型別不符時就會發生)。  
  
2.  依需要重複步驟 1 來建立完整的基本運算質輸入連結集 (可能不是整個輸入參數集)。  
  
    > [!NOTE]
    >  少數運算質不需要任何輸入連結。 例如，**日期**，**時間**，和**日期和時間**中的運算質**日期和時間**運算質類別提供目前的日期時間或日期和時間，分別在正在處理的執行個體訊息的。 因此，它們不需要來源結構描述的任何輸入參數。  
  
    > [!NOTE]
    >  許多運算質的輸入參數的順序相當重要，因為對應的運算質參考主題所指示 (請參閱**運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)])。 您建立連結的順序將會設定運算質的輸入參數順序。 如需運算質屬性和指定的運算質輸入參數順序的詳細資訊，請參閱[編輯運算質屬性和輸入參數](../core/editing-functoid-properties-and-input-parameters.md)。 如需如何設定運算質的輸入的參數資訊，請參閱[如何設定運算質輸入參數](../core/how-to-configure-functoid-input-parameters.md)。  
  
    > [!NOTE]
    >  在開始連結之前，請確定要連結的運算質或來源結構描述節點可以在顯示的格線頁或來源結構描述視窗中看到。  
  
## <a name="create-the-output-link-from-a-basic-functoid"></a>建立基本運算質的輸出連結  
  
1.  將記錄或欄位節點從目的結構描述拖曳至顯示的格線頁中的基本運算質。  
  
     **-或者-**  
  
     在顯示的格線頁中，將另一個位於右邊較遠的運算質拖曳至您要建立輸出連結的基本運算質。  
  
     **-或者-**  
  
     將顯示的格線頁中的基本運算質拖曳至目的結構描述中的記錄或欄位節點。  
  
     **-或者-**  
  
2.  在顯示的格線頁中，將您要建立輸出連結的基本運算質拖曳另一個位於右邊較遠的運算質。  
  
    > [!NOTE]
    >  在開始連結作業之前，請確定要連結的運算質或來源結構描述節點可以在顯示的格線頁和來源結構描述視窗中看到。  
  
    > [!NOTE]
    >  運算質連結永遠會嘗試不允許不適當的連結，例如來源和目標資料型別不符的連結。  
  
    > [!NOTE]
    >  在拖曳時，與錨定的連結結束點相對的移動連結結束點，會變成十字形狀圖示以允許更精確地鎖定第二個結束點。 若您將移動的連結結束點暫留在不適當的第二個連結結束點的物件上，十字形狀圖示就會變成有斜線劃過的圓圈圖示 (例如，當資料型別不符時就會發生)。  
  
## <a name="see-also"></a>另請參閱  
**運算質參考**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]