
                            git config user.email "fariyajshaikh86@gmail.com"
                            git config user.name "Mfariyaj"
                        
                            imageTag=$(grep -oE 'backend:[[:space:]]*[0-9]+' deployment.yaml | awk -F':' '{print $2}' | xargs)
                            echo "Current image tag: $imageTag"
                            
                            sed -i "s|image: .*|image: ${REPOSITORY_URI}${AWS_ECR_REPO_NAME}:${BUILD_NUMBER}|" deployment.yaml
                        
                            echo "Updated deployment.yaml contents:"
                            
                            cat deployment.yaml
                        
                            git diff deployment.yaml  # Debugging to check if sed made changes
                        
                            git add -A  # Ensure all changes are staged
                            git status  # Debugging to verify staged files
                        
                            git commit -m "Update deployment Image to version ${BUILD_NUMBER}" || echo "No changes to commit"
                            git push https://${GITHUB_TOKEN}@github.com/${GIT_USER_NAME}/${GIT_REPO_NAME} HEAD:main
                        