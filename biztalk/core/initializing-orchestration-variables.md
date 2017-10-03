---
title: "初始化協調流程變數 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: orchestrations, variables
ms.assetid: 770e4e55-1fb9-4b43-854c-63aec5a3c5ba
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a90fbc33343e3576d6199a0a97a7a57ca881f720
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="initializing-orchestration-variables"></a>初始化協調流程變數
您可以在 [屬性] 視窗中設定屬性，初始化變數的值。 例如，您可以設定**初始值**設為 32，初始化 System.Int32 類型的變數。 將初始值加入至字串類型的變數時，您必須在 [屬性] 視窗中將初始值括在引號內。 若要讓字串包含引號，請使用反斜線做為逸出字元，若要在字串中包含常值反斜線時，則請使用連續的反斜線做為逸出字元。 如果未指定變數的值，一旦建立協調流程的執行個體時，就會指定預設值給變數。  
  
 如果變數是類別的執行個體，您可以指定建構函式，將它初始化。 根據預設，**使用預設建構函式**屬性設定為**True**如果預設建構函式功能; 因此，預設建構函式會呼叫。 如果您只想要使用預設建構函式，您不需要再次初始化變數中的**運算式**圖形，以避免兩次呼叫建構函式。 如果**使用預設建構函式**屬性設定為**False**，將不會呼叫預設建構函式; 您必須在運算式中呼叫建構函式，或將它指派給變數，才能使用它在您的協調流程。 此外，如果建構函式需要輸入的參數，您必須設定**使用預設建構函式**至**False** ，然後呼叫建構函式從**運算式**圖形; 針對範例中， `myVariable = myNamespace.myClass (param1, param2)`。  
  
 您才能明確初始化變數的唯一情況是當您的協調流程包含多個啟動接收，盡可能在**範圍**，**平行動作**或**接聽**圖形。 在此情況下，已停用自動初始化，而且您必須使用**運算式**圖形來初始化變數。 您必須將**運算式**圖形和每個啟動接收之後，協調流程中存取任何變數之前。