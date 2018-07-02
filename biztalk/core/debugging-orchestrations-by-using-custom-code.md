---
title: 偵錯協調流程使用自訂程式碼 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, debugging
- building, debugging
ms.assetid: 94e569fa-8dea-4027-abb5-37b4a8015621
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e32358f48099b9d184a9ff1ff62a0a85af595b89
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995335"
---
# <a name="debugging-orchestrations-by-using-custom-code"></a>使用自訂程式碼偵錯協調流程
如果您的協調流程會在測試環境或您正在建立原型並想要修改訊息欄位和協調流程變數的值，您可以將輸出寫入[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]中使用下列程式碼的主控台**運算式**圖形：  
  
```  
System.Diagnostics.Debug.WriteLine(iResult);  
```  
  
 您需要將這**運算式**立即執行作業，以便您可以將輸出進行偵錯結果的圖形之後的圖形。  
  
 或者，您也可以建立偵錯 DLL，撰寫簡單的自訂偵錯工具，在這個偵錯 DLL 裡所用的類別必須可以將輸入視為訊息，而且這個訊息的格式必須已在協調流程中定義並為偵錯 DLL 所參考。 如需有關如何將訊息傳遞做為參數的詳細資訊，請參閱[如何使用運算式建立物件和呼叫物件方法](../core/how-to-use-expressions-to-create-objects-and-call-object-methods.md)。  
  
 此方法會顯示具有下拉式方塊或其他控制項的對話方塊，可讓使用者修改值，然後將編輯好的訊息放在一起，並傳回為傳回值。  
  
 設定布林值變數，以指出您的協調流程是否處於偵錯模式，則只要您有一個點在您想要能夠修改值的協調流程中，您可以加入**決定**具有一個即時圖形只有當您偵錯模式變數設為 True，或您想要檢查的特定條件發生時執行的分支。 呼叫您的方法，從**運算式**圖形中的即時分支**決定**。 當您不再需要偵錯時，偵錯模式變數設為 False，或移除**決定**圖形完全並重新編譯。  
  
## <a name="to-debug-a-net-component-called-by-an-orchestration"></a>偵錯協調流程呼叫的 .NET 元件  
 下列步驟示範如何偵錯協調流程呼叫的 .NET 元件：  
  
1. 開啟元件的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。  
  
2. 在協調流程呼叫的方法上設定您元件的中斷點。  
  
3. 按一下 **偵錯**功能表，然後選取**附加至處理序...** 若要顯示**附加至處理序**對話方塊。  
  
4. 按一下 **選取...** 下一步按鈕**附加至：** 文字方塊中，以顯示**選取程式碼類型**對話方塊。  
  
5. 按一下以選取的選項**偵錯這些程式碼類型：** ，然後選取**受控**，然後按一下 [**確定**] 按鈕。  
  
6. 按一下以選取**BTSNTSvc.exe**處理序**可用的處理序**，然後按一下 [**附加**] 按鈕。  
  
7. 透過接收埠將訊息傳送到您的協調流程。  
  
8. .NET 元件應該在中斷點上停止。  
  
9. 您可以跟平常一樣使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 執行偵錯。  
  
    > [!NOTE]
    >  若要取得最佳結果，應該在全域組件快取 (GAC) 中註冊 .NET 元件。  
  
## <a name="see-also"></a>另請參閱  
 [協調流程偵錯工具使用者介面](../core/orchestration-debugger-user-interface.md)   
 [偵錯協調流程](../core/debugging-orchestrations.md)