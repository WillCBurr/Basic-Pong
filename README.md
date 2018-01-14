# Basic-Pong
A simple Xcode Pong
import SpriteKit
import GameplayKit

class GameScene: SKScene {
    
    var ball = SKSpriteNode()
    var Enemy = SKSpriteNode()
    var Main = SKSpriteNode()
    
    override func didMove(to view: SKView) {
        ball = self.childNode(withName: "ball") as! SKSpriteNode
        Enemy = self.childNode(withName: "Enemy") as! SKSpriteNode
        Main = self.childNode(withName: "Main") as! SKSpriteNode
        
        ball.physicsBody?.applyImpulse(CGVector(dx: 20, dy: 20))
        
        let border = SKPhysicsBody(edgeLoopFrom: self.frame)
        border.friction = 0
        border.restitution = 1
        
        self.physicsBody = border
        
    }
    override func touchesBegan(_ touches: Set<UITouch>, with event: UIEvent?) {
        
        
for touch in touches{
    let location = touch.location(in: self)
    
   Main.run(SKAction.moveTo(x: location.x, duration: 0.2))
        }
    }
    
    override func touchesMoved(_ touches: Set<UITouch>, with event: UIEvent?) {
        for touch in touches{
        let location = touch.location(in: self)
                
    Main.run(SKAction.moveTo(x: location.x, duration: 0.2))
            }
    }
    
    override func update(_ currentTime: TimeInterval) {

        Enemy.run(SKAction.moveTo(                       x: ball.position.x, duration: 1.0))
    }

}
