---
title: "如何更新組件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4f456c8f-247a-4d5c-b5af-41e88968779c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 163b06706652b1f65b9a76e3feea8911a2ca4c88
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-update-an-assembly"></a>如何更新組件
本主題說明如何更新組件和組件使用 Visual Studio 2010 部署的應用程式的版本。  
  
> [!NOTE]  
>  如果您是以新版本來更新組件，就不需要重新啟動應用程式。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。  
  
## <a name="updating-an-assembly"></a>更新組件  
  
#### <a name="to-increment-the-version-number-of-an-assembly"></a>要遞增組件的版本號碼  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案，然後**屬性**。  
  
2.  在**專案設計工具**，按一下 [**應用程式**] 索引標籤。  
  
3.  在右窗格中，按一下 **組件資訊**。  
  
4.  在**組件資訊**對話方塊方塊中，指定的值**組件版本**增加組件版本號碼的欄位。 您只應該增加主要或次要的版本號碼。 主要版本號碼是序列中的第一個數字 (***n***.0.0.0); 的次要版本號碼是序列中的第二位數 (0。***n ***.0.0)。 BizTalk Server 將無法辨識版本號碼變更為序列，例如 0.0 後面。*** n ***.0 或 0.0.0。***n***.  
  
5.  按一下**確定**關閉**組件資訊** 對話方塊。  
  
6.  儲存專案。  
  
    > [!NOTE]  
    >  使用「管線設計師」和「BizTalk 總管物件模型」，避免在遞增組件版本時發生結構描述衝突。  
  
#### <a name="to-change-the-application-that-an-assembly-is-deployed-to"></a>若要變更組件部署到應用程式  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案，然後**屬性**。  
  
2.  在**專案設計工具**，按一下 [**部署**] 索引標籤。  
  
3.  在右窗格中，應用程式中指定名稱**應用程式名稱**欄位。  
  
4.  請確認**安裝到全域組件快取**屬性設定為**True**。  
  
    > [!NOTE]  
    >  當您部署方案時，組件將會部署到新的應用程式中，並且安裝在 GAC 內。